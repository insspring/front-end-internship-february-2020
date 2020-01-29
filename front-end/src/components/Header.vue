<template>
    <div class="header">
        <button class="signUpBtn" @click="visibleUp = !visibleUp">{{ $t('signUp') }}</button>
        <div class="signUp" v-if="visibleUp">
            <div class="signUpContent">
                <span class="close" @click="visibleUp = !visibleUp">X</span>
                <div class="inputFields">
                    <span>{{ $t('name') }}</span>
                    <input v-model="name" type="text" placeholder="Name">
                    <span>{{ $t('email') }}</span>
                    <input v-model="email" type="email" placeholder="your@yours.com">
                    <span>{{ $t('password') }}</span>
                    <input v-model="password" type="password">
                    <button @click="createPerson()" type="submit">{{ $t('submit') }}</button>
                </div>
            </div>
        </div>
        <button class="signInBtn" @click="visibleIn = !visibleIn">{{ $t('signIn') }}</button>
        <div class="signIn" v-if="visibleIn">
            <div class="signInContent">
                <span class="close" @click="visibleIn = !visibleIn">X</span>
                <div class="inputFields">
                    <span>{{ $t('email') }}</span>
                    <input v-model="email" type="email" placeholder="your@yours.com">
                    <span>{{ $t('password') }}</span>
                    <input v-model="password" type="password">
                    <button @click="logPerson()" type="submit">{{ $t('submit') }}</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: "Header",
        data() {
            return {
                visibleUp: false,
                visibleIn: false,
                name: null,
                email: null,
                password: null,
                users: []
            }
        },
        methods: {
            createPerson() {
                if(this.name && this.email && this.password) {
                    let person = {
                        name: this.name,
                        email: this.email,
                        password: this.password,
                    };
                    this.name = null;
                    this.email = null;
                    this.password = null;
                    this.users.push(person);
                    this.visibleUp = false;
                    alert("You've been successfully signed up!")
                } else alert('Error');
            },

        }
    }
</script>

<style scoped>
    .signUp, .signIn {
        position: fixed;
        z-index: 1;
        padding-top: 100px;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
        background-color: rgba(0,0,0,0.7);
    }
    .signUpBtn, .signInBtn {
        margin: .5rem;
        padding: 1rem;
        border-radius: 1em;
        border: none;
        color: white;
        font-weight: bold;
        font-family: Arial;
        background-color: rgb(161, 15, 8);
        cursor: pointer;
    }
    .signUpBtn:hover, .signInBtn:hover {
        background-color: rgb(130, 10, 4);
    }
    .signUpContent, .signInContent {
        background-color: white;
        margin: auto;
        padding: 2rem;
        border: 1px solid grey;
        width: 20%;
        border-radius: 1.5rem;
    }
    .close {
        color: gray;
        float: right;
        font-size: 1rem;
        font-weight: bold;
    }
    .close:hover {
        color: black;
        cursor: pointer;
    }
    .inputFields {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    input {
        margin: 1rem 0;
    }
</style>