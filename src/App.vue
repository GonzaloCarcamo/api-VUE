<template>
        <div>
                <h1>API - jsonplaceholder</h1>
                <table>
                        <tbody>
                                <th>ID</th>
                                <th>Name</th>
                                <th>Username</th>
                                <th>Email</th>
                                <tr v-for="todo in todos" :key="todo.id">
                                        <td>{{todo.id }}</td>
                                        <td>{{todo.name }}</td>
                                        <td>{{todo.username }}</td>
                                        <td>{{todo.email }}</td>
                                </tr>
                        </tbody>
                </table>
        </div>
</template>

<script>

import axios from 'axios'

export default {
        data(){
                return {
                        todos:null
                }
        },

        mounted(){
                console.log('hola desde mounted');
                this.getTodos();
        },

        methods: {
                getTodos(){
                        console.log('get todos');
                        axios.get('https://jsonplaceholder.typicode.com/users')
                        .then( response => {
                                this.todos = response.data;
                        })
                        .catch( e => console.log(e))
                }
        }
}
</script>

<style>
        *{
                font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                text-align: justify;
        }
        table{
                width: 600px;
        }

        th{
                background: rgb(220, 220, 255);
                font-weight: 800;
                text-align: center;
        }

        td{
                border: 1px dashed rgb(163, 159, 159);
        }
</style>