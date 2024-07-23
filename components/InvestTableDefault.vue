<template>
    <div class="invest-table">
        <h2 class="text-my-blue font-semibold mb-4 text-5xl">Акции</h2>
        <div class="invest-table__wrapper p-4">
            <div class="invest-table__body">
                <table class="min-w-full  border-collapse">
                    <thead>
                    <tr>
                        <th class="px-4 pb-5 text-left">Инструмент</th>
                        <th class="px-4 pb-5 text-left">Обновление</th>
                        <th class="px-4 pb-5 text-left">Позиция</th>
                        <th class="px-4 pb-5 text-left">Комиссия (₽)</th>
                        <th class="px-4 pb-5 text-left">Фин. рез. (₽)</th>
                        <th class="px-4 pb-5 text-left">Просадка (₽)</th>
                        <th class="px-4 pb-5 text-left">Плечо</th>
                    </tr>
                    </thead>
                    <tbody>
                    <tr
                        v-for="stock in stocks"
                        :key="stock.instrument"
                    >
                        <td class="px-4 py-2 text-my-blue">{{ stock.instrument }}</td>
                        <td class="px-4 py-2 text-my-blue">{{ stock.update }}</td>
                        <td class="px-4 py-2 text-my-blue">{{ stock.position }}</td>
                        <td class="px-4 py-2 text-my-blue">{{ stock.commission }}</td>
                        <td
                            :class="['px-4 py-2 ', stock.financialResult > 0 ? 'text-green-500' : 'text-red-500']"
                        >
                            {{ stock.financialResult }}
                        </td>
                        <td class="px-4 py-2 text-my-blue">{{ stock.drawdown }}</td>
                        <td class="px-4 py-2 text-my-blue">{{ stock.leverage }}</td>
                    </tr>
                    </tbody>
                </table>
            </div>
            <div class="flex justify-center items-center mt-4 text-lg invest-table__footer">
                <div class="text-my-white">Комиссия: <span class="text-my-blue">{{ totalCommission.toFixed(2) }}  ₽</span></div>
                <div class="dot mx-2">
                    <svg width="4" height="4" viewBox="0 0 4 4" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="2" cy="2" r="2" fill="#031138"/>
                    </svg>
                </div>
                <div class="text-my-white">Фин. результат: <span class="text-my-blue">{{ totalResult.toFixed(2) }} ₽</span></div>
            </div>
        </div>
    
    </div>
</template>

<script setup>
const stocks = [
    {
        instrument: 'GAZP',
        update: '20:20:28 24-06-24',
        position: 644,
        commission: 0,
        financialResult: 426216.4,
        drawdown: -6000000,
        leverage: 10,
    },
    {
        instrument: 'SBER',
        update: '20:20:28 24-06-24',
        position: 532,
        commission: 334.43,
        financialResult: -360232.68,
        drawdown: -6000000,
        leverage: 10,
    },
    {
        instrument: 'TATNP',
        update: '20:20:28 24-06-24',
        position: 32915,
        commission: 0,
        financialResult: 10371.1,
        drawdown: -6000000,
        leverage: 10,
    },
]

const totalCommission = stocks.reduce((acc, stock) => acc + stock.commission, 0)
const totalResult = stocks.reduce((acc, stock) => acc + stock.financialResult, 0)
</script>
