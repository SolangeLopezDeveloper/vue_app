<template>
    <h1>¿Deseas buscar una receta?</h1>
    <input type="text" class="searchInput" v-model="search" v-on:keyup.enter="searchData" placeholder="Buscar receta...">

    <Meal v-for="meal in meals" v-bind:key="meal.idMeal" v-bind:meal="meal" :meals="meals" />

    <div class="text-center">
        ...
    </div>

    <h3>
        O busca por categoría
    </h3>

    <Category v-for="category in paginated" :key="category.idCategory" v-bind:category="category" />


    <div class="text-center">
        Actual: {{ current }}
    </div>

    <div class="text-center">
        <a @click="prev()">Anterior</a> |
        <a @click="next()">Siguiente</a>

    </div>
</template>
<script>
import Category from './Category.vue';
import Meal from './Meal.vue';
import axios from 'axios';
import Swal from 'sweetalert2';
export default {
    name: 'App',
    components: {
        Category,
        Meal
    },
    data() {
        return {
            categories: [],
            meals: [],
            search: null,
            current: 1,
            pageSize: 5
        }
    },

    mounted() {
        axios.get('https://themealdb.com/api/json/v1/1/categories.php')
            .then((response) => {
                //idCategory,strCategory,strCategoryDescription, strCategoryThumb
                this.categories = response.data.categories
            })
            .catch((error) => { console.log(error) })
    },
    computed: {
        indexStart() {
            return (this.current - 1) * this.pageSize;
        },
        indexEnd() {
            return this.indexStart + this.pageSize
        },
        paginated() {
            return this.categories.slice(this.indexStart, this.indexEnd)
        }
    },
    methods: {
        searchData() {
            //Verifico si el campo de búsqueda tiene texto
            if (this.search) {
                axios.get('https://themealdb.com/api/json/v1/1/search.php?s=' + this.search)
                    .then((response) => {
                        this.meals = response.data.meals;
                    })
                    .catch((error) => {
                        console.log(error);
                    })
            } else {
                Swal({
                    title: "Atención",
                    text: "Debes ingresar un texto",
                    icon: "error"
                })



            }
        },
        prev() {
            this.current--;
        },
        next() {
            this.current++;
        }
    }
}
</script>