<script>
export default {
    data() {
        return {
            months: { 1: "Ocak", 2: "Şubat", 3: "Mart", 4: "Nisan" },
            weekDays: { 1: "Pazartesi", 2: "Salı", 3: "Çarşamba", 4: "Perşembe", 5: "Cuma", 6: "Cumartesi", 0: "Pazar" },
            date: new Date(),
            dateText: null
        }
    },
    computed: {
        dateTextCmp: {
            get: function() {
                return this.formatDate(new Date());
            },
            set: function(val) {
                this.dateText = val;
            }
        }
    },
    methods: {
        nextDay() {
            this.date.setDate(this.date.getDate() + 1);
            this.dateTextCmp = this.formatDate(this.date);
        },
        formatDate(dt) {
            return dt.getDate() + " " + this.months[dt.getMonth()+1] + " " + dt.getFullYear() + ", " + this.weekDays[dt.getDay()];
        }
    }
}
</script>

<template>

    <div class="top-bar d-flex flex-row justify-space-between align-center pa-8">
        <div class="date-area">
            {{ dateText ?? dateTextCmp }} 
        </div>

        <div class="next-button">
            <v-btn @click="nextDay" append-icon="mdi-chevron-right">
            Sonraki Gün
            </v-btn>
        </div>
    </div>

</template>

<style scoped>
.top-bar {
    background-color: #336B87;
}

.date-area {
    color: white
}

.next-button {
}
</style>