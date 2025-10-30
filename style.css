const container = document.getElementById('puzzle-container');
const shuffleBtn = document.getElementById('shuffle-btn');
const resetBtn = document.getElementById('reset-btn');

// --- Game Data ---
let tiles = [1,2,3,4,5,6,7,8,null]; // null = empty tile
let moveCount = 0;
let timer = 0;
let timerInterval;

// --- Create Info Displays ---
const infoBox = document.createElement('div');
infoBox.classList.add('info');
document.querySelector('.container').appendChild(infoBox);

const moveCounter = document.createElement('p');
moveCounter.id = 'moveCounter';
moveCounter.textContent = 'Moves: 0';
infoBox.appendChild(moveCounter);

const timerDisplay = document.createElement('p');
timerDisplay.id = 'timer';
timerDisplay.textContent = 'Time: 0s';
infoBox.appendChild(timerDisplay);

// --- Main Functions ---
function createTiles() {
  container.innerHTML = '';
  tiles.forEach((num, i) => {
    const tile = document.createElement('div');
    tile.classList.add('tile');
    if (num === null) {
      tile.classList.add('empty');
    } else {
      tile.textContent = num;
      tile.style.background = getColor(num);
      tile.addEventListener('click', () => moveTile(i));
    }
    container.appendChild(tile);
  });
}

function getColor(num) {
  const colors = [
    '#f94144', '#f3722c', '#f8961e', '#f9844a',
    '#43aa8b', '#4d908e', '#577590', '#277da1'
  ];
  return colors[num - 1];
}

function moveTile(index) {
  const emptyIndex = tiles.indexOf(null);
  const validMoves = [index - 3, index + 3]; // up or down
  if (index % 3 !== 0) validMoves.push(index - 1); // left
  if (index % 3 !== 2) validMoves.push(index + 1); // right

  if (validMoves.includes(emptyIndex)) {
    [tiles[index], tiles[emptyIndex]] = [tiles[emptyIndex], tiles[index]];
    moveCount++;
    moveCounter.textContent = "Moves: " + moveCount;
    createTiles();
    checkWin();
  }
}

function shuffle() {
  do {
    tiles.sort(() => Math.random() - 0.5);
  } while (!isSolvable());
  createTiles();
  resetStats();
  startTimer();
}

function isSolvable() {
  const arr = tiles.filter(n => n !== null);
  let invCount = 0;
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[i] > arr[j]) invCount++;
    }
  }
  return invCount % 2 === 0;
}

function reset() {
  tiles = [1,2,3,4,5,6,7,8,null];
  createTiles();
  resetStats();
  clearInterval(timerInterval);
}

function resetStats() {
  moveCount = 0;
  moveCounter.textContent = "Moves: 0";
  timer = 0;
  timerDisplay.textContent = "Time: 0s";
}

function startTimer() {
  clearInterval(timerInterval);
  timerInterval = setInterval(() => {
    timer++;
    timerDisplay.textContent = "Time: " + timer + "s";
  }, 1000);
}

function checkWin() {
  const correct = [1,2,3,4,5,6,7,8,null];
  if (JSON.stringify(tiles) === JSON.stringify(correct)) {
    clearInterval(timerInterval);
    setTimeout(() => {
      alert("🎉 You solved it in " + moveCount + " moves and " + timer + " seconds!");
    }, 200);
  }
}

// --- Button Events ---
shuffleBtn.addEventListener('click', shuffle);
resetBtn.addEventListener('click', reset);

// --- Start Game ---
createTiles();