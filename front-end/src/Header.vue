<template>
    <div class="header">
        <button @click="visibleUp = !visibleUp"
                @keyup.esc="visibleUp = false">{{ $t('signUp') }}</button>
        <div class="signUp" v-if="visibleUp">
            <div class="signForm">
                <span>{{ $t('name') }}</span>
                <input type="name" placeholder="Name">
                <span>{{ $t('email') }}</span>
                <input type="email" placeholder="your@yours.com">
                <span>{{ $t('password') }}</span>
                <input type="password">
            </div>
        </div>
        <button @click="visibleIn = !visibleIn"
                @keyup.esc="visibleIn = false">{{$t('signIn')}}</button>
        <div class="signIn" v-if="visibleIn">
            <div class="signForm">
                <span>{{ $t('email') }}</span>
                <input type="email" placeholder="your@yours.com">
                <span>{{ $t('password') }}</span>
                <input type="password">
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
            }
        },
    }
</script>

<style scoped>
    .signUp,.signIn {
        width:100%;
        height: 2000px;
        background-color: rgba(0,0,0,0.7);
        position:fixed;
        top:0;
    }
    .signForm {
        background: white;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 10%;
        margin: 15rem auto;
        padding: 3rem;
        border-radius: .5rem;
        text-align: center;
    }
    input {

    }

</style>