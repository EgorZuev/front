<template>
<div class="home">

    <div class="container">
        <h1>Список пользователей</h1>
        <div class="d-grid gap-2 col-2 mx-auto my-3">
            <button @click="GetUsers()" type="button" class="btn btn-outline-secondary">Обновить</button>
        </div>
    </div>

    <div class="container">
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th scope="col">Id</th>
                    <th scope="col">FullName</th>
                    <th scope="col">Email</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in responce" :key="user.id">
                    <td scope="row">{{ user.id }}</td>
                    <td>{{ user.fullName }}</td>
                    <td>{{ user.email }}</td>
                </tr>
            </tbody>
        </table>
    </div>

</div>
</template>

<script lang="ts">
import {
    Component,
    Vue
} from "vue-property-decorator";
import axios from "axios"
import {
    BootstrapVue,
    IconsPlugin
} from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)
Vue.use(IconsPlugin)

@Component({
    components: {},
})

export default class Home extends Vue {
    responce = []

    async GetUsers() {
        const result = await axios.get('http://localhost:4015/users');
        this.responce = result.data.data
    }
}
</script>
