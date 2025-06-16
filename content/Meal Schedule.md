<%*
const daysOfWeek = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];
const meals = ['Breakfast', 'Lunch', 'Dinner'];

let scheduleHtml = '<div class="meal-schedule">';

for (const day of daysOfWeek) {
    scheduleHtml += `<div class="day-column"><h3>${day}</h3>`;
    for (const meal of meals) {
        scheduleHtml += `<div class="meal-slot" data-day="${day}" data-meal="${meal}">
            <h4>${meal}</h4>
            <div class="recipe-drop" ondrop="drop(event)" ondragover="allowDrop(event)"></div>
        </div>`;
    }
    scheduleHtml += '</div>';
}

scheduleHtml += '</div>';

// Add CSS for the grid layout
const css = `
<style>
.meal-schedule {
    display: flex;
    overflow-x: auto;
}
.day-column {
    min-width: 200px;
    border: 1px solid #ccc;
    margin: 5px;
    padding: 10px;
}
.meal-slot {
    border: 1px dashed #999;
    margin: 5px 0;
    padding: 5px;
    min-height: 100px;
}
.recipe-drop {
    min-height: 50px;
    border: 1px dotted #666;
}
</style>
`;

// Add JavaScript for drag and drop functionality
const javascript = `
<script>
function allowDrop(ev) {
    ev.preventDefault();
}

function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
}

function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
</script>
`;

tR += css + scheduleHtml + javascript;
%>