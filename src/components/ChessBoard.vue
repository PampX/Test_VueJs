<template>
    <div class="board">
        <div v-for="(row, rowIndex) in board" :key="rowIndex" class="row">
            <div v-for="(cell, colIndex) in row" :key="colIndex" class="cell" :class="getCellColor(rowIndex, colIndex)">
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
        };
    },
    methods: {
        getCellColor(row, col) {
            return (row + col) % 2 === 0 ? 'light' : 'dark';
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
</style>