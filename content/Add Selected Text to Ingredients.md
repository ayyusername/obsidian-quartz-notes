<%*
const fs = require('fs');
const path = require('path');

const ingredientsPath = path.join(app.vault.adapter.basePath, 'data', 'ingredients.json');

// Get the selected text
const selectedText = tp.file.selection();

// Read the existing JSON file
let ingredients = [];
if (fs.existsSync(ingredientsPath)) {
  const data = fs.readFileSync(ingredientsPath, 'utf-8');
  ingredients = JSON.parse(data);
}

// Append the selected text to the ingredients array
if (selectedText && !ingredients.includes(selectedText)) {
  ingredients.push(selectedText);
}

// Write the updated array back to the JSON file
fs.writeFileSync(ingredientsPath, JSON.stringify(ingredients, null, 2), 'utf-8');

// Provide feedback to the user
new Notice('Added selected text to ingredients');
%>
