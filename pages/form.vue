<template>
    <div class="container">
    <section class="form">
        <form v-on:submit.prevent="handleSubmit">
        <div class="field">
            <label class="label">Nama Lengkap</label>
            <div class="control">
                <input v-model="form.name" class="input" type="text"
                 placeholder="Nama lengkap beserta gelar">
            </div>
            <label class="label">Select Inquiry</label>
            <div class="control">
                <select v-model="form.inquiry_type">
                <option v-for="option in options.inquiry" v-bind:key="option.value">
                {{ option.text }}</option>
            </select>
            </div>
            <div class="control">
                <button class="button is-primary">Submit</button>
            </div>
        </div>
        </form>
    </section>

    <section class="content">
        <br>
        <ul>
            <li v-for="(item, abc) in form" :key="abc">
                <strong> {{ abc }}:</strong> {{ item }}
            </li>
        </ul>
    </section>

    <div>
        <h3>Hasil Submit Form</h3>
        <ul>
            <li v-for="item in inputanForm" :key="item">
            {{ form }}</li>
        </ul>
    </div>
    </div>
</template>

<script>
    export default {
        layout (context) {
            return 'custom'
        },
        data() {
            return {
                form: {
                    name: '',
                    message:'',
                    inquiry_type: '',
                    usecases:[],
                    terms: false,
                    concepts:[],
                    js_awesome:''
                },
                options: {
                    inquiry: [
                        { value: 'feature', text: "Feature Request"},
                        { value: 'bug', text: "Bug Report"},
                        { value: 'support', text: "Support Saja"}
                    ]
                },
                inputanForm: [],
                heightInp: null,
                inpValSubmitted: 'Not submitted yet'
            }
        },
        methods: {
            handleSubmit() {
                // console.log(this.form)
                const item = {
                    form: this.form
                }
                this.inputanForm.push(item)
            },
            registerAnswer() {
                if(this.heightInp) {
                    this.inpValSubmitted = this.heightInp + ' cm';
                }
            }
        }
    }
</script>