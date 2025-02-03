const gameCells = document.querySelectorAll('.cell');
const player1 = document.querySelector('.player1');
const player2 = document.querySelector('.player2');
const restartBtn = document.querySelector('.restartBtn');
const alertBox = document.querySelector('.alertBox');

// making variables
let currentPlayer = 'X';
let nextPlayer = 'O'
let PlayerTurn = currentPlayer;

player1.textContent = `player 1: ${currentPlayer}`;
player2.textContent = `playre 2:${nextPlayer}`;

// function to start your function
const startGame = () => {
    gameCells.forEach(cell => {
        cell.addEventListener('click', handleClick);
    });

}

const handleClick = (e) => {
    if (e.target.textContent === '') {
        e.target.textContent = PlayerTurn;
        if (checkwin()) {
            showAlert(`${PlayerTurn} is winner !`);
            disableCells();
        }
        else if (checkTie()) {
            showAlert('It is tie!');
            disableCells();
        }
        else {
            changePlayerTurn();
            showAlert(`Turn for player: ${PlayerTurn}`);
        }

    }
}

// function to change the player turn 
const changePlayerTurn = () => {
    PlayerTurn = PlayerTurn === currentPlayer ? nextPlayer : currentPlayer;

}

// function to check win
const checkwin = () => {
    const winningConditions = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6],

    ];
    for (let i = 0; i < winningConditions.length; i++) {
        const [pos1, pos2, pos3] = winningConditions[i];
        if (gameCells[pos1].textContent !== '' &&
            gameCells[pos1].textContent === gameCells[pos2].textContent &&
            gameCells[pos2].textContent == gameCells[pos3].textContent) {
            return true;

        }

    }
    return false;
}
// function to check tie
const checkTie = () => {
    let emptyCellsCount = 0;
    gameCells.forEach(cell => {
        if (cell.textContent === '') {
            emptyCellsCount++;
        }
    });
    return emptyCellsCount === 0 && !checkwin();
}
// function for disable 
const disableCells = () => {
    gameCells.forEach(cell => {
        cell.removeEventListener('click', handleClick);
        cell.classList.add('disabled');
    });
}
// function for restartBtn
const restartGame = () => {
    gameCells.forEach(cell => {
        cell.textContent='';
        cell.classList.remove('disabled');
    });
    startGame();
}
restartBtn.addEventListener('click', restartGame);

const showAlert=(msg)=>{
    alertBox.textContent=msg;
    alertBox.style.display="block";
    setTimeout(()=>{
        alertBox.style.display="none";
    },8000);
}
startGame();
