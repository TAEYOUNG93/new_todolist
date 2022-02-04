<template>
  <div class="date">
        {{ month }}/{{ date }} {{ day }}
  </div>
</template>

<script>
export default {
    data() {
        return {
            month: 0,
            date: 0,
            week: ['Mon','Tue','Wed','Thu','Fri','Sat','Sun'],
            day: ''
        }
    },
    methods: {
        getDate() {
            const date = new Date();
            this.month = date.getMonth() + 1;
            this.date = date.getDate();
            this.day = this.week[date.getDay() - 1];

        }
    },
    mounted() {
        setInterval(() => {
            this.getDate();
        }, 800);
    }
}
</script>

<style scoped>
.date {
    display: flex;
    justify-content: flex-end;
    color: white;
    height: 60px;
    padding: 20px 30px;
    font-size: 40px;
    font-weight: 600;
}

</style>