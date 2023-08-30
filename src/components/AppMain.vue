<template>
    <div class="container">
        <h1>
            Latest Projects
        </h1>
        <div class="projects">
            <div class="card" v-for="project in projects">
                <img src="" class="card-img-top" alt="...">
                <div class="card-body">
                    <h5 class="card-title">{{project.title}}</h5>
                    <p class="card-text">{{project.repo}}</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {    
    name:'AppMain',
    data() {
        return {
            projects : [],
            apiUrl : 'http://127.0.0.1:8000/api/projects'
        }
    },
    methods: {
        getProjects(){
            axios.get(this.apiUrl, {
                params: {}
            })
            .then((response) => {
                console.log(response.data.data)
                this.projects = response.data.data;
            })
            .catch(function (error) {
                console.log(error);
            })
        }
    },

    created(){
        this.getProjects();
    }
}

</script>

<style lang="scss">
    
</style>