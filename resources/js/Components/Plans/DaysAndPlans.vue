<script setup>
import { ref } from 'vue';
import { format, addDays, subDays } from 'date-fns';
import { es } from 'date-fns/locale';

const currentDate = ref(new Date());

const formatDate = (date) => {
    return {
        day: format(date, 'd', { locale: es }),
        month: format(date, 'MMMM', { locale: es }),
        weekday: format(date, 'EEEE', { locale: es })
    };
};

const formattedDateToday = ref(formatDate(currentDate.value));
const formattedDateYesterday = ref(formatDate(subDays(currentDate.value, 1)));
const formattedDateTomorrow = ref(formatDate(addDays(currentDate.value, 1)));

const updateDates = () => {
    formattedDateToday.value = formatDate(currentDate.value);
    formattedDateYesterday.value = formatDate(subDays(currentDate.value, 1));
    formattedDateTomorrow.value = formatDate(addDays(currentDate.value, 1));
};

const changeDay = (days) => {
    currentDate.value.setDate(currentDate.value.getDate() + days);
    updateDates();
};
</script>

<template>
    <div>
        <div class="w-full flex justify-center items-center mt-5 gap-5">
            <!-- Botón para día anterior -->
            <button @click="changeDay(-1)" class="p-3 bg-sky-500 text-white rounded-lg">Anterior</button>
            
            <!-- Día de Ayer -->
            <div class="border rounded-lg">
                <div class="bg-sky-500 w-64 h-16 flex justify-center items-center rounded-t-lg">
                    <p class="text-4xl font-black">{{ formattedDateYesterday.month }}</p>
                </div>
                <div class="w-64 h-24 flex justify-center items-center">
                    <p class="text-7xl font-black text-sky-500">{{ formattedDateYesterday.day }}</p>
                </div>
                <div class="w-64 flex justify-center items-center mb-5">
                    <p class="text-2xl text-sky-500 font-black">{{ formattedDateYesterday.weekday }}</p>
                </div>
            </div>

            <!-- Día Actual -->
            <div class="border rounded-lg">
                <div class="bg-sky-500 w-64 h-16 flex justify-center items-center rounded-t-lg">
                    <p class="text-4xl font-black">{{ formattedDateToday.month }}</p>
                </div>
                <div class="w-64 h-24 flex justify-center items-center">
                    <p class="text-7xl font-black text-sky-500">{{ formattedDateToday.day }}</p>
                </div>
                <div class="w-64 flex justify-center items-center mb-5">
                    <p class="text-2xl text-sky-500 font-black">{{ formattedDateToday.weekday }}</p>
                </div>
            </div>

            <!-- Día de Mañana -->
            <div class="border rounded-lg">
                <div class="bg-sky-500 w-64 h-16 flex justify-center items-center rounded-t-lg">
                    <p class="text-4xl font-black">{{ formattedDateTomorrow.month }}</p>
                </div>
                <div class="w-64 h-24 flex justify-center items-center">
                    <p class="text-7xl font-black text-sky-500">{{ formattedDateTomorrow.day }}</p>
                </div>
                <div class="w-64 flex justify-center items-center mb-5">
                    <p class="text-2xl text-sky-500 font-black">{{ formattedDateTomorrow.weekday }}</p>
                </div>
            </div>
            
            <!-- Botón para día siguiente -->
            <button @click="changeDay(1)" class="p-3 bg-sky-500 text-white rounded-lg">Siguiente</button>
        </div>
    </div>
</template>
