<script>
export default {
    data() {
        return {

        }
    },
    mounted() {
        this.goCreate();
    },
    methods: {
        goCreate() {
            this.$router.push({name: 'create'})
        },
        goNotes() {
            this.$router.push({name: 'notes'})
        },
        goStatistics() {
            this.$router.push({name: 'statistics'})
        }
    }
}
</script>
<template>
    <div class="app-header mb-3">
        <button @click="goNotes" :class="{'active': $route.name == 'notes'}" class="btn btn-outline-secondary">
            Записи
        </button>

        <button @click="goCreate" :class="{'active': $route.name == 'create'}" class="btn btn-outline-secondary">
            +
        </button>

        <button @click="goStatistics" :class="{'active': $route.name == 'statistics'}" class="btn btn-outline-secondary">
            Статистика
        </button>

    </div>
</template>

<style>
.app-header {
    display: flex;
    gap: 10px;
    justify-content: center;
    padding: 30px 0;

    position: sticky;
    top: 0;
    z-index: 1;
    background-color: white;
    border-bottom: 1px dashed black;
}

.app-header button {
    flex: 1;
}
</style>