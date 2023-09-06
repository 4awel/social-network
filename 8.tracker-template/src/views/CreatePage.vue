<script>
import axios from 'axios';
import dayjs from 'dayjs';

export default {
    data() {
        return {
            date: '',
            description: '',
            category: '',
            title: '',
            isVisible: false,
            isVisibleFall: false
        }
    },
    mounted() {

    },
    methods: {
        async sendData() {
            await axios.post('/notes/create', {
                date: this.date,
                description: this.description,
                category: this.category,
                title: this.title
            });
        },

        emoties(evt) {
            evt.preventDefault();
            if (this.category == 1) {
                this.title = 'Плохо';
                this.sendData()
                this.isVisible = true
                this.isVisibleFall = false;
            } else if (this.category == 2) {
                this.title = 'Не очень';
                this.sendData()
                this.isVisible = true
                this.isVisibleFall = false;
            } else if (this.category == 3) {
                this.title = 'Нормально';
                this.sendData()
                this.isVisible = true
                this.isVisibleFall = false;
            } else if (this.category == 4) {
                this.title = 'Хорошо';
                this.sendData()
                this.isVisible = true
                this.isVisibleFall = false;
            } else if (this.category == 5) {
                this.title = 'Супер';
                this.sendData()
                this.isVisible = true
                this.isVisibleFall = false;
            } else {
                this.isVisibleFall = true;
            }
        },

    },
}
</script>


<template>
    <div class="create-page">
        <h3 class="mb-5">Как вы себя чувствуете?</h3>

        <form @submit="emoties">
            <div class="input-group">
                <span class="input-group-text">Время</span>
                <input v-model="date" type="datetime-local" class="form-control">
            </div>

            <div class="categories-container my-5">
                <label class="category">
                    <input v-model="category" class="category-input" type="radio" value="5">
                    <div class="category-info">
                        <img src="src/assets/5.svg">
                        Супер
                    </div>
                </label>
                <label class="category">
                    <input v-model="category" class="category-input" type="radio" value="4">
                    <div class="category-info">
                        <img src="src/assets/4.svg">
                        Хорошо
                    </div>
                </label>
                <label class="category">
                    <input v-model="category" class="category-input" type="radio" value="3">
                    <div class="category-info">
                        <img src="src/assets/3.svg">
                        Нормально
                    </div>
                </label>
                <label class="category">
                    <input v-model="category" class="category-input" type="radio" value="2">
                    <div class="category-info">
                        <img src="src/assets/2.svg">
                        Не очень
                    </div>
                </label>
                <label class="category">
                    <input v-model="category" class="category-input" type="radio" value="1">
                    <div class="category-info">
                        <img src="src/assets/1.svg">
                        Плохо
                    </div>
                </label>
            </div>

            <div class="note-container">
                <div class="form-floating note-input-container">
                    <textarea v-model="description" class="form-control note-input" placeholder="Заметка"
                        id="note"></textarea>
                    <label for="note">Заметка</label>
                </div>

                <button class="btn btn-outline-secondary" type="submit">
                    Сохранить
                </button>

            </div>
            <div v-if="isVisibleFall" class="alert alert-danger" role="alert">
                Вы не выброли настроение!
            </div>
            <div v-if="isVisible" class="alert alert-success" role="alert">
                Ваше настроение добавлено :)
            </div>

        </form>
    </div>
</template>


<style>
.create-page h3 {
    text-align: center;
}

.create-page .category {
    display: flex;
    flex-direction: column;
    width: 20%;
    align-items: center;
    justify-content: center;
}

.category {
    position: relative;
}

.category img {
    width: 60%;
}

.category-input {
    display: none;
}


.category-info {
    display: flex;
    flex-direction: column;
    gap: 10px;
    align-items: center;
    justify-content: center;
    padding: 10px;

    transition: scale 300ms;
}

/* Выбранная радиокнопка */
.category .category-input:checked~.category-info {
    scale: 1.4;
}

.categories-container {
    display: flex;
}

.note-container {
    display: flex;
    gap: 10px;
    justify-content: space-between;
}

.note-container .note-input-container {
    flex: 1;
}
</style>