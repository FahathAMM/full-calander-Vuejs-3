<template>
    <div class="container m-auto">
        <h1 class="text-6xl text-center">Calendar</h1>
        <section>
            <section class="mx-8 flex justify-between">
                <h2 class="font-bold text-3xl">{{ currentMonthName }}</h2>
                <h2 class="font-bold text-3xl">{{ currentYear }}</h2>
            </section>
            <div class="flex justify-center mt-4">
                <p
                    class="uppercase text-3xl text-center font-black"
                    style="width:14.28%"
                    v-for="day in days"
                    :key="day"
                >{{ day }}</p>
            </div>
        </section>
        <section class="flex flex-wrap my-4">
            <p
                class="text-center text-2xl my-4 font-black"
                style="width:14.28%"
                v-for="num in startDay()"
                :key="num"
            ></p>

            <p
                class="text-center text-2xl my-4 font-black"
                style="width:14.28%"
                v-for="num in daysInMonth()"
                :key="num"
                :class="currentDay(num)"
            >{{ num }}</p>
        </section>
        <section class="mx-8 flex justify-between mt-9">
            <button class="py-2 px-4 border rounded" @click="prev">Prev</button>
            <button class="py-2 px-4 border rounded" @click="next">Next</button>
        </section>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentYear: new Date().getFullYear(),
            currentMonth: new Date().getMonth(),
            days: ['sun', 'mon', 'tue', 'wen', 'thu', 'fri', 'sat'],
            ff: '',
        }
    },
    created() {
        // this.next();
    },

    methods: {
        daysInMonth() {
            return new Date(this.currentYear, this.currentMonth + 1, 0).getDate();
        },

        startDay() {
            return new Date(this.currentYear, this.currentMonth - 1).getDay();
        },

        next() {
            if (this.currentMonth == 11) {
                this.currentMonth = 0;
                this.currentYear++;
            } else {
                this.currentMonth++;
            }
        },

        prev() {
            if (this.currentMonth == 0) {
                this.currentMonth = 11;
                this.currentYear--;
            } else {
                this.currentMonth--;
            }
        },

        currentDay(num) {
            const calenderFullDate = new Date(this.currentYear, this.currentMonth, num).toDateString();
            const currentFullDate = new Date().toDateString();
            return calenderFullDate == currentFullDate ? 'text-blue-400' : ''
        },

    },
    computed: {
        currentMonthName() {
            return new Date(this.currentYear, this.currentMonth).toLocaleString("default", { month: 'long' })
        }
    }
}
</script>

<style>
</style>