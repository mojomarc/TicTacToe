const board = document.getElementById("game-board");
const statusText = document.getElementById("status");
let currentPlayer = "X";
let gameState = ["", "", "", "", "", "", "", "", ""];
let gameActive = true;

function handleCellClick(index) {
    if (!gameActive || gameState[index] !== "") return;

    gameState[index] = currentPlayer;
    renderBoard();

    if (checkWinner()) {
        statusText.textContent = `Player ${currentPlayer} wins!`;
        gameActive = false;
    } else if (!gameState.includes("")) {
        statusText.textContent = "It's a draw!";
        gameActive = false;
    } else {
        currentPlayer = currentPlayer === "X" ? "O" : "X";
        statusText.textContent = `Player ${currentPlayer}'s turn`;
    }
}

function checkWinner() {
    const winPatterns = [
        [0,1,2], [3,4,5], [6,7,8],
        [0,3,6], [1,4,7], [2,5,8],
        [0,4,8], [2,4,6]
    ];
    return winPatterns.some(pattern => {
        const [a, b, c] = pattern;
        return gameState[a] && gameState[a] === gameState[b] && gameState[a] === gameState[c];
    });
}

function renderBoard() {
    board.innerHTML = "";
    gameState.forEach((cell, index) => {
        const div = document.createElement("div");
        div.classList.add("cell");
        div.textContent = cell;
        div.addEventListener("click", () => handleCellClick(index));
        board.appendChild(div);
    });
}

function resetGame() {
    gameState = ["", "", "", "", "", "", "", "", ""];
    currentPlayer = "X";
    gameActive = true;
    statusText.textContent = `Player ${currentPlayer}'s turn`;
    renderBoard();
}

renderBoard();
statusText.textContent = `Player ${currentPlayer}'s turn`;
