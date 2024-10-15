const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

let block = {
    x: 50,
    y: 50,
    size: 30,
    color: 'blue'
};

function drawBlock() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = block.color;
    ctx.fillRect(block.x, block.y, block.size, block.size);
}

function moveBlock(dx, dy) {
    block.x += dx;
    block.y += dy;

    // Keep the block within the canvas bounds
    block.x = Math.max(0, Math.min(canvas.width - block.size, block.x));
    block.y = Math.max(0, Math.min(canvas.height - block.size, block.y));

    drawBlock();
}

document.addEventListener('keydown', (event) => {
    switch (event.key) {
        case 'ArrowUp':
            moveBlock(0, -10);
            break;
        case 'ArrowDown':
            moveBlock(0, 10);
            break;
        case 'ArrowLeft':
            moveBlock(-10, 0);
            break;
        case 'ArrowRight':
            moveBlock(10, 0);
            break;
    }
});

// Initial draw
drawBlock();
