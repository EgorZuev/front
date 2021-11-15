<template>
<div class="messages">

    <div class="container">
        <div class="row justify-content-center mb-3">
            <form class="col-6 row justify-content-center">

                <div class="mb-3 text-start">
                    <label for="inputEmail2" class="form-label">Email</label>
                    <input v-model="form.email" type="tex" class="form-control" id="inputEmail2" aria-describedby="emailHelp" placeholder="mail@mail.ru" />
                    <div id="emailHelp" class="form-text">Введите ваш Email адрес</div>
                </div>
                <div class="mb-3 text-start">
                    <label for="inputMessage1" class="form-label">Message</label>
                    <textarea v-model="form.message" class="form-control" id="inputMessage1" rows="3" placeholder="Сообщение" />
                    </div>
                <button @click="send()" type="button" class="btn btn-outline-secondary">Отправить</button>

            </form>
        </div>
        {{responce}}
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

export default class Messages extends Vue {
    responce = ""

    form = {
        email: "",
        message: ""
    }

    async send() {
        try {
            const result = await axios.post('http://localhost:4015/users/messages', this.form);
            this.responce = result.data
        } catch {
            this.responce = "Ошибка валидации"
        }
    }
}
</script>
