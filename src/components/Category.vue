<template>
    <div class="container-category">
        <div class="row-md-6">
            <div class="card mb-3 category_container" style="width: 45rem;" @click="openCategoryList">
                <img v-bind:src="category.strCategoryThumb" v-bind:alt="category.strCategory" width="200">
                <div class="card-body">
                    <h6 class="card-title">{{ category.strCategory }}</h6>
                    <p class="card-text">{{ category.strCategoryDescription }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ["category"],
    methods: {
        openCategoryList() {
            this.$router.push("/category/" + this.category.strCategory)

        }
    }
}
</script> 