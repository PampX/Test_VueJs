<template>
    <div class="board">
        <div v-for="(row, rowIndex) in board" :key="rowIndex" class="row">
            <div v-for="(cell, colIndex) in row" :key="colIndex" class="cell"
                :class="[getCellColor(rowIndex, colIndex), isSelected(rowIndex, colIndex) ? 'selected' : '']"
                @click="handleClick(rowIndex, colIndex)">
                {{ cell }}
            </div>

        </div>
    </div>
</template>

<script>
export default {
    name: 'ChessBoard',
    data() {
        return {
            board: [
                ['♜', '♞', '♝', '♛', '♚', '♝', '♞', '♜'],
                ['♟', '♟', '♟', '♟', '♟', '♟', '♟', '♟'],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['♙', '♙', '♙', '♙', '♙', '♙', '♙', '♙'],
                ['♖', '♘', '♗', '♕', '♔', '♗', '♘', '♖']
            ],
            selectedCell: null,
        };
    },
    methods: {
        getCellColor(row, col) {
            return (row + col) % 2 === 0 ? 'light' : 'dark';
        },
        isSelected(row,col){
            return this.selectedCell && 
            this.selectedCell.row === row &&
            this.selectedCell.col === col
        },
        handleClick(row,col){
            const cellContent = this.board[row][col];

            if (this.selectedCell === null) {
                // step 1 : select a piece
                if (cellContent !== '') {
                    this.selectedCell = {row,col}
                }
            } else {
                // step 2 : move the piece 
                const from = this.selectedCell
                const piece = this.board[from.row][from.col]

                // simple move
                this.board[row][col] = piece
                this.board[from.row][from.col] = ''

                // reset 
                this.selectedCell = null
            }
        }
    }
};
</script>

<style scoped>
.board {
    display: grid;
    grid-template-rows: repeat(8, 60px);
    gap: 0;
}

.row {
    display: grid;
    grid-template-columns: repeat(8, 60px);
}

.cell {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    font-weight: bold;
}

.light {
    background-color: #f0d9b5;
}

.dark {
    background-color: #b58863;
}

.selected {
    z-index: 1000;
    outline: 3px solid yellow;
}
</style>