<script>
import axios from 'axios';
import dayjs from 'dayjs';

export default {
    data() {
        return {
            notes: [],
        }
    },
    mounted() {
        this.loadNotes()
    },
    methods: {
        async loadNotes() {
            const response = await axios('/notes/all');
            this.notes = response.data;
        },
        getDate(date) {
            let day = dayjs(date);
            return day.format("dddd, D MMMM, HH:mm");
        }
    },
}
</script>

<template>
    <div class="calendar-page">
        <div class="card my-3">
            <div v-for="(item, index) in notes" class="card-body">
                <img :src="'/src/assets/'+ item.category +'.svg'">

                <div>
                    <div class="note-title">
                        {{ item.title }}
                    </div>
                    <div class="note-date">
                        {{ getDate(item.date) }}
                    </div>
                    <p class="note-text">
                        {{ item.description }}
                    </p>
                </div>
            </div>

        </div>
    </div>
</template>


<style>
.calendar-page .card-body {
    display: flex;
    gap: 40px;
    align-items: flex-start;
}

.calendar-page img {
    width: 100px;
}

.calendar-page .note-title {
    font-weight: bold;
    text-transform: uppercase;
    font-size: 24px;
    ;
}

.calendar-page .note-date {
    text-transform: lowercase;
    color: #6c757d;
}

.calendar-page .note-text {
    margin-top: 10px;
}
</style>