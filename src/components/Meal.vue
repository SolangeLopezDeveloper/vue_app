<template >
    <div class="container">
        <div class="row">
            <div class="col-md-6" >
                <div class="card mb-3">
                    <img @click="openMealDetails" v-bind:src="meal.strMealThumb" v-bind:alt="meal.strMeal" width="300">
                    <p><b>{{ meal.strMeal }}</b></p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["meal"],
    methods: {
        openMealDetails() {
            this.$router.push("/meal/" + this.meal.idMeal)

        }
    }

}
</script>