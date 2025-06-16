# Obsidian Templater Script for Recipe Management

## Project Overview

Develop an Obsidian Templater script for recipe management. The script should process recipe notes, identify ingredients, create links to corresponding ingredient notes, and update master lists for both ingredients and recipes.

## System Setup

- Operating System: macOS 10.13.6 (High Sierra)
- Hardware: MacBook Air (13-inch, Mid 2011)
- Processor: 1.7 GHz Intel Core i5
- Memory: 4 GB 1333 MHz DDR3
- Obsidian Version: 1.6.3 (Installer 1.4.13)
- Templater Version: 2.3.3

## File Structure

- Vault root: /Users/josh/Library/Mobile Documents/iCloud/Obsidian/Atlas/
- Templates folder: /Users/josh/Library/Mobile Documents/iCloud/Obsidian/Atlas/General Obsidian Admin/Obsidian Files/Templater/
- Scripts folder: /Users/josh/Library/Mobile Documents/iCloud/Obsidian/Atlas/General Obsidian Admin/Templater/Templater User Scripts/
- Recipes folder: /Users/josh/Library/Mobile Documents/iCloud/Obsidian/Atlas/210 Recipes/
- Ingredients folder: /Users/josh/Library/Mobile Documents/iCloud/Obsidian/Atlas/210 Recipes/Ingredients

## Requirements

1. Process recipe notes to identify ingredients and create links to ingredient notes.
2. Create ingredient notes when they don't exist.
3. Update a master ingredient list with new ingredients.
4. Update a master recipe list with new recipes.
5. Handle alternative forms of ingredients (e.g., plural, variations).
6. Implement both dry run and actual execution modes.
7. Provide robust error handling and logging.
8. Ensure efficient processing without causing Obsidian to freeze.
9. Follow proper file naming and path conventions:
   - Ingredient pages should be written to Atlas/210 Recipes/Ingredients/
   - File names should have natural spaces without hyphens
   - File names should not end with ".md" within the file name
   - File names should be capitalized at the beginning
10. Correctly update ingredient mentions to links in the recipe text.
11. Work within Templater's limitations (e.g., recursion limit for file creation).

## Lessons Learned

1. Templater has a recursion limit (max = 10) for creating new files.
2. Complex regex operations can cause performance issues.
3. Asynchronous operations need careful handling within Templater.
4. Ingredient matching needs to be flexible to handle various forms and contexts.
5. File path and naming conventions are crucial for consistency.
6. The script needs to handle both ingredient file creation and recipe text updating simultaneously.
7. Dry run mode should accurately preview changes without modifying files.

## Recent Error Log

The most recent version of the script worked correctly in dry run mode but failed to update the ingredient mentions to links when actually applied, although it did create the proper ingredient files.

## Key Requirements for the Solution

1. Efficient ingredient detection and matching algorithm.
2. Robust error handling to prevent script termination.
3. Careful management of file creation to avoid hitting Templater's recursion limit.
4. Proper handling of asynchronous operations.
5. Clear and informative logging for debugging.
6. Ability to process complex recipes without freezing Obsidian.
7. Correct application of changes to the original recipe file, including updating ingredient mentions to links.
8. Proper file naming and path conventions as specified.

## Sample Recipe for Testing

Use the "Vegan Beef Wellington" recipe provided in the project files for testing the script.

## Task

Create a comprehensive Obsidian Templater script that addresses all the requirements and incorporates the lessons learned. The script should:

1. Be written in JavaScript, compatible with Obsidian's Templater plugin.
2. Include clear comments and version information.
3. Implement both dry run and actual execution modes.
4. Correctly handle ingredient detection, linking, and file creation.
5. Update both the ingredient files and the recipe text links.
6. Provide clear logging and error handling.
7. Follow the specified file naming and path conventions.
8. Be efficient and avoid causing Obsidian to freeze.

Please provide a complete, executable script that addresses all these points, with a focus on correctly updating both the ingredient files and the recipe text links in both dry run and actual execution modes.

Here is the code: 

<%*
// Version 2.3.1: Recipe Management Script with Improved File Naming, Paths, and Link Updates

// Configuration
const CONFIG = {
    DEBUG: true,
    DRY_RUN: true, // Set to false to apply changes
    INGREDIENTS_FOLDER: "Atlas/210 Recipes/Ingredients",
    MASTER_INGREDIENT_LIST: "Atlas/210 Recipes/Master Ingredient List.md",
    MASTER_RECIPE_LIST: "Atlas/210 Recipes/Master Recipe List.md"
};

// Ingredient list (expanded with some variations)
const ingredients = {
    "artichoke": ["artichokes"],
    "arugula": ["rocket"],
    "asparagus": ["asparagus spears"],
    "olive oil": ["extra virgin olive oil", "evoo"],
    "onion": ["onions"],
    "garlic": ["garlic cloves"],
    "carrot": ["carrots"],
    "celery": ["celery stalks"],
    "mushroom": ["mushrooms"],
    "walnut": ["walnuts"],
    "rice": ["brown rice"],
    "soy sauce": [],
    "thyme": ["dried thyme"],
    "rosemary": ["dried rosemary"],
    "puff pastry": ["vegan puff pastry"],
    "almond milk": [],
    "spinach": ["fresh spinach"],
    "shallot": ["shallots"],
    "salt": ["salt to taste"],
    "pepper": ["black pepper"]
};

// Utility functions
function log(message) {
    console.log(message);
    tR += message + "\n";
}

function formatFileName(name) {
    return name.split(' ')
        .map(word => word.charAt(0).toUpperCase() + word.slice(1))
        .join(' ');
}

function createIngredientLink(ingredient) {
    const fileName = formatFileName(ingredient);
    return `[[${CONFIG.INGREDIENTS_FOLDER}/${fileName}|${ingredient}]]`;
}

async function createIngredientFile(ingredient) {
    const fileName = formatFileName(ingredient);
    const filePath = `${CONFIG.INGREDIENTS_FOLDER}/${fileName}.md`;
    if (!await tp.file.exists(filePath)) {
        if (!CONFIG.DRY_RUN) {
            await tp.file.create_new(`# ${ingredient}\n\nAdd details about ${ingredient} here.`, filePath);
            log(`Created new ingredient file: ${filePath}`);
        } else {
            log(`DRY RUN: Would create new ingredient file: ${filePath}`);
        }
    }
}

async function updateMasterList(item, listPath) {
    const listFile = tp.file.find_tfile(listPath);
    if (!listFile) {
        if (!CONFIG.DRY_RUN) {
            await tp.file.create_new(`# Master List\n\n- [[${item}]]`, listPath);
            log(`Created new master list: ${listPath}`);
        } else {
            log(`DRY RUN: Would create new master list: ${listPath}`);
        }
        return;
    }
    const content = await app.vault.read(listFile);
    if (!content.includes(`- [[${item}]]`)) {
        if (!CONFIG.DRY_RUN) {
            await app.vault.modify(listFile, content + `\n- [[${item}]]`);
            log(`Added ${item} to ${listPath}`);
        } else {
            log(`DRY RUN: Would add ${item} to ${listPath}`);
        }
    }
}

// Main processing function
async function processRecipe(content) {
    log("Starting recipe processing");
    let processedContent = content;
    let ingredientsFound = 0;
    let changes = [];

    for (const [mainIngredient, variations] of Object.entries(ingredients)) {
        const allForms = [mainIngredient, ...variations];
        const regex = new RegExp(`\\b(${allForms.join('|')})\\b`, 'gi');
        
        let match;
        let hasChanged = false;
        while ((match = regex.exec(processedContent)) !== null) {
            ingredientsFound++;
            const originalText = match[0];
            const linkedText = createIngredientLink(mainIngredient);
            processedContent = processedContent.slice(0, match.index) + linkedText + processedContent.slice(match.index + originalText.length);
            regex.lastIndex += linkedText.length - originalText.length;
            hasChanged = true;
        }
        
        if (hasChanged) {
            changes.push(`Linked "${mainIngredient}" and its variations`);
            await createIngredientFile(mainIngredient);
            await updateMasterList(`${CONFIG.INGREDIENTS_FOLDER}/${formatFileName(mainIngredient)}`, CONFIG.MASTER_INGREDIENT_LIST);
        }
    }

    log(`Total ingredients found: ${ingredientsFound}`);
    return { processedContent, changes };
}

// Main execution
try {
    const originalContent = tp.file.content;
    log(`Original content length: ${originalContent.length} characters`);

    const { processedContent, changes } = await processRecipe(originalContent);

    log(`Processed content length: ${processedContent.length} characters`);

    if (changes.length > 0) {
        log("Changes detected in the recipe:");
        changes.forEach(change => log(`- ${change}`));

        if (!CONFIG.DRY_RUN) {
            const userConfirmation = await tp.system.prompt("Apply these changes? (yes/no)", "yes");
            if (userConfirmation.toLowerCase() === "yes") {
                await app.vault.modify(tp.file.find_tfile(tp.file.path(true)), processedContent);
                await updateMasterList(tp.file.path(true), CONFIG.MASTER_RECIPE_LIST);
                log("File updated and added to master recipe list");
            } else {
                log("Changes were not applied as per user choice");
            }
        } else {
            log("DRY RUN: Changes were not applied. Here's a preview of the changes:");
            log(processedContent);
        }
    } else {
        log("No changes were made to the recipe");
    }
} catch (error) {
    log(`An error occurred: ${error.message}`);
}

// Change Log:
// v2.3.1 - Ensured text-to-link updates are working correctly
// v2.3.0 - Updated file paths to include "Atlas/" prefix
//        - Modified file naming to use spaces and proper capitalization
//        - Removed ".md" from internal file names (kept for actual file creation)
// v2.2.0 - Fixed issue with recipe content modification
//        - Improved dry run mode to prevent actual file changes
//        - Enhanced logging to show actual content changes
//        - Improved ingredient matching and linking process
%>


