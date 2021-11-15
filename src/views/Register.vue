<template>
<div class="register">

    <div class="container">

        <div class="row justify-content-center">
            <form class="col-6 row justify-content-center">

                <div class="mb-3 text-start">
                    <label for="fullName1" class="form-label">ФИО</label>
                    <input v-model="form.fullName" type="tex" class="form-control" id="fullName1" placeholder="Иванов Иван Иванович" />
                </div>
                <div class="mb-3 text-start">
                    <label for="inputEmail1" class="form-label">Email</label>
                    <input v-model="form.email" type="tex" class="form-control" id="inputEmail1" placeholder="mail@mail.ru" />
                </div>
                <div class="mb-3 text-start">
                    <label for="inputPassword1" class="form-label">Пароль</label>
                    <input v-model="form.password" type="tex" class="form-control" id="inputPassword1" placeholder="Пароль" />
                </div>
                <button @click="register()" type="button" class="btn btn-outline-secondary">Зарегистрироваться</button>

            </form>
        </div>

        {{response}}

    </div>

</div>
</template>

<script lang="ts">
import {
    Component,
    Vue
} from "vue-property-decorator";
import axios from "axios"

@Component({
    components: {},
})

export default class Register extends Vue {
    form = {
        fullName: "",
        email: "",
        password: ""
    }
    response = "";

    async register() {
        try {
            const result = await axios.post('http://localhost:4015/users', this.form);
            this.response = result.data
        } catch {
            this.response = "Ошибка валидации"
        }
    }
}
</script>
