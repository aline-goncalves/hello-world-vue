<template>
    <header>
        <h1>
            <img src="../assets/logo.jpg" alt="">
        </h1>
        <button class="button" @click="changeTheme">{{ changeButtonText }}</button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'LateralBar',
    emits: ['whenThemeChanged'],
    data () {
        return{
           isDarkModeActive: false 
        }
    },
    computed:{
        changeButtonText(){
            if(this.isDarkModeActive){
                return 'Desativar modo esturo'
            }
            return 'Ativar modo esturo'
        }
    },
    methods:{
        changeTheme(){
            this.isDarkModeActive = !this.isDarkModeActive
            this.$emit('whenThemeChanged', this.isDarkModeActive)
        }
    }
})
</script>

<style scoped>
header{
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}
@media only screen and (max-width: 768px){
    header{
        padding: 2.5rem;
        height: auto;
    }
}
img{
    border-radius: 1rem;
}
</style>