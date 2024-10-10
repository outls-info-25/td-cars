<template>
    <div class="container">
        <h1>Liste de Voitures</h1>

        <div class="add-car-form">
            <input v-model="newCar.marque" :class="{ 'input-error': inputErrors.marque }" type="text"
                placeholder="Marque" />
            <input v-model="newCar.type" :class="{ 'input-error': inputErrors.type }" type="text" placeholder="Type" />
            <input v-model="newCar.annee" :class="{ 'input-error': inputErrors.annee }" type="text"
                placeholder="Année" />
            <button @click="addCar">Ajouter Voiture</button>
        </div>

        <div class="content">
            <div class="car-list">
                <div v-for="(car, index) in cars" :key="index" class="car-item"
                    :class="['car-item', { selected: selectedCar === car }]" @click="selectCar(car)">
                    <span class="car-info">{{ car.marque }}</span>
                    <button class="delete-button" @click.stop="deleteCar(index)">
                        <span>&#10006;</span>
                    </button>
                </div>
            </div>

            <div class="car-details">
                <h2>Détails de la Voiture</h2>
                <div v-if="selectedCar">
                    <p><strong>Marque:</strong> {{ selectedCar?.marque }}</p>
                    <p><strong>Type:</strong> {{ selectedCar?.type }}</p>
                    <p><strong>Année:</strong> {{ selectedCar?.annee }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';

const cars = ref([
    { marque: 'Toyota', type: 'SUV', annee: '2020' },
    { marque: 'Honda', type: 'Berline', annee: '2018' },
    { marque: 'Ford', type: 'Pickup', annee: '2019' },
    { marque: 'Chevrolet', type: 'SUV', annee: '2021' },
    { marque: 'BMW', type: 'Berline', annee: '2017' },
    { marque: 'Mercedes', type: 'Coupé', annee: '2016' },
    { marque: 'Audi', type: 'SUV', annee: '2020' },
    { marque: 'Volkswagen', type: 'Hatchback', annee: '2019' },
    { marque: 'Kia', type: 'SUV', annee: '2021' },
    { marque: 'Hyundai', type: 'Berline', annee: '2018' },
    { marque: 'Nissan', type: 'SUV', annee: '2020' },
    { marque: 'Subaru', type: 'Berline', annee: '2017' },
    { marque: 'Volvo', type: 'SUV', annee: '2022' },
    { marque: 'Tesla', type: 'Électrique', annee: '2021' },
    { marque: 'Porsche', type: 'Coupé', annee: '2019' },
]);

const selectedCar = ref(null);

const newCar = ref({
    marque: '',
    type: '',
    annee: ''
});

const inputErrors = ref({
    marque: false,
    type: false,
    annee: false
});

const selectCar = (car) => {
    selectedCar.value = car;
};

const deleteCar = (index) => {
    cars.value.splice(index, 1);
};

const addCar = () => {
    inputErrors.value.marque = !newCar.value.marque;
    inputErrors.value.type = !newCar.value.type;
    inputErrors.value.annee = !newCar.value.annee;

    if (newCar.value.marque && newCar.value.type && newCar.value.annee) {
        cars.value.push({ ...newCar.value });
        newCar.value.marque = '';
        newCar.value.type = '';
        newCar.value.annee = '';
    }
};
</script>

<style scoped>
.container {
    width: 80vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
    font-family: 'Arial', sans-serif;
}

h1 {
    margin-bottom: 20px;
    font-size: 2rem;
    color: #333;
}

/* possible d'utiliser .add-car-form .input-error */
.input-error {
    border: 2px solid red !important; 
}

.add-car-form {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

.add-car-form input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 150px;
}

.add-car-form button {
    padding: 10px 15px;
    border: none;
    background-color: #4CAF50;
    color: white;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.add-car-form button:hover {
    background-color: #45a049;
}

.content {
    display: flex;
    gap: 50px;
    width: 100%;
    justify-content: space-around;
}

.car-list {
    display: flex;
    flex-direction: column;
    width: 40%;
}

.car-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 15px;
    margin: 5px 0;
    background-color: #f9f9f9;
    cursor: pointer;
    border-radius: 8px;
    border: 1px solid #ddd;
    text-align: center;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.selected {
    background-color: #cce5ff;
    border: 2px solid #007bff;
    transform: scale(1.05);
}

.car-info {
    flex-grow: 1;
}

.delete-button {
    background-color: red;
    color: white;
    border: none;
    padding: 5px 10px;
    cursor: pointer;
}

.delete-button:hover {
    background-color: darkred;
}

.car-item:hover {
    background-color: #e0e0e0;
    transform: scale(1.05);
}

.car-details {
    width: 40%;
    border: 1px solid #ddd;
    padding: 20px;
    background-color: #f7f7f7;
    border-radius: 8px;
    height: 200px;
}

.car-details h2 {
    margin-bottom: 10px;
}

.car-details p {
    margin: 5px 0;
}
</style>