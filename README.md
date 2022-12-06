// Create a color wheel element
let colorWheel = document.createElement('div');
colorWheel.className = 'color-wheel';

// Add the color wheel to the page
document.body.appendChild(colorWheel);

// Define an array of colors to include on the color wheel
let colors = [  [255, 0, 0], // Red
  [255, 165, 0], // Orange
  [255, 255, 0], // Yellow
  [0, 255, 0], // Green
  [0, 0, 255], // Blue
  [75, 0, 130], // Indigo
  [238, 130, 238] // Violet
];

// Create a color picker for each color
colors.forEach((color, i) => {
  let colorPicker = document.createElement('div');
  colorPicker.className = 'color-picker';
  colorPicker.style.backgroundColor = `rgb(${color[0]}, ${color[1]}, ${color[2]})`;
  colorPicker.addEventListener('click', () => selectColor(i));
  colorWheel.appendChild(colorPicker);
});

// Define the selected colors
let selectedColors = [null, null];

// Define the selected color elements
let selectedColorElements = [];

// Create the selected color elements
selectedColors.forEach((color, i) => {
  let selectedColorElement = document.createElement('div');
  selectedColorElement.className = 'selected-color';
  selectedColorElement.addEventListener('click', () => selectColor(i));
  selectedColorElements.push(selectedColorElement);
  document.body.appendChild(selectedColorElement);
});

// Define the result element
let resultElement = document.createElement('div');
resultElement.className = 'result';
document.body.appendChild(resultElement);

// Select a color
function selectColor(i) {
  // Store the selected color
  selectedColors[i] = colors[i];

  // Update the selected color element
  selectedColorElements[i].style.backgroundColor = `rgb(${selectedColors[i][0]}, ${selectedColors[i][1]}, ${selectedColors[i][2]})`;

  // Update the result element
  if (selectedColors[0] && selectedColors[1]) {
    // Combine the RGB values of the two colors
    let result = [      selectedColors[0][0] + selectedColors[1][0],
      selectedColors[0][1] + selectedColors[1][1],
      selectedColors[0][2] + selectedColors[1][2]
    ];

    // Update the result element
    resultElement.style.backgroundColor = `rgb(${result[0]}, ${result[1]}, ${result[2]})`;
  }
}
