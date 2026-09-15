<template>
    <div class="container">
        <div class="card"></div>
        <div class="card"></div>
        <div class="card"></div>

        <div class="card"></div>
        <div class="card"></div>
    </div>
</template>

<style>

.container {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    gap: 20px;
    margin: 50px auto;
}

.card {
    height: 200px;
    background-color: #252525;
    border: 2px solid #444;
    border-radius: 15px;

    transition: transform 0.1s, box-shadow 0.1s;
}

.card:hover {
    transform: translateX(5px) translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0, 0.7);
}

.card:nth-child(1),
.card:nth-child(2),
.card:nth-child(3) {
    grid-column: span 2;
}

.card:nth-child(4),
.card:nth-child(5) {
    grid-column: span 3;
}

</style>