<script>
import axios from 'axios';
import dayjs from 'dayjs';

export default {
    data() {
        return {
            statistics5: [],
            statistics4: [],
            statistics3: [],
            statistics2: [],
            statistics1: [],
            super: '',
            good: '',
            normal: '',
            notgood: '',
            badly: ''
        }
    },
    mounted() {
        this.loadSuper();
        this.loadGood();
        this.loadNormal();
        this.loadNotgood();
        this.loadBadly();
    },
    methods: {
        async loadSuper() {
            const response = await axios('/statistics/super');
            this.statistics5 = response.data
            this.super = this.statistics5.length
        },
        async loadGood() {
            const response = await axios('/statistics/good');
            this.statistics4 = response.data
            this.good = this.statistics4.length
        },
        async loadNormal() {
            const response = await axios('/statistics/normal');
            this.statistics3 = response.data
            this.normal = this.statistics3.length
        },
        async loadNotgood() {
            const response = await axios('/statistics/notgood');
            this.statistics2 = response.data
            this.notgood = this.statistics2.length
        },
        async loadBadly() {
            const response = await axios('/statistics/badly');
            this.statistics1 = response.data
            this.badly = this.statistics1.length
        },
    },
}
</script>
<template>
    <div class="container">
        <h2>Сводка</h2>
        <div class="container-item">
            <div class="item">
                <b>{{ super }}</b>
                <img src="../assets/5.svg" alt="">
                <p>Супер</p>
            </div>
            <div class="item">
                <b>{{ good }}</b>
                <img src="../assets/4.svg" alt="">
                <p>Хорошо</p>
            </div>
            <div class="item">
                <b>{{ normal }}</b>
                <img src="../assets/3.svg" alt="">
                <p>Нормально</p>
            </div>
            <div class="item">
                <b>{{ notgood }}</b>
                <img src="../assets/2.svg" alt="">
                <p>Не очень</p>
            </div>
            <div class="item">
                <b>{{ badly }}</b>
                <img src="../assets/1.svg" alt="">
                <p>Плохо</p>
            </div>
        </div>
        <hr>
    </div>
</template>
<style>
    .container {
        padding: 24px;
    }

    h2 {
        font-size: 30px;
        text-align: center;
    }

    .container-item {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        padding: 10px;
        margin: 4px;
    }

    .item {
        display: flex;
        flex-direction: column;
        gap: 40px;
        align-items: center;
        padding: 0 24px;
    } 

    img {
        height: 70px;
    }
    
    b {
        font-size: 28px;
    }

</style>