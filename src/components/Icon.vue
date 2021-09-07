<template>
    <div @mouseenter="animate()" @mouseleave="animate()" class="grow box column is-10">
        <button @click="$emit('delete-icon')" class="delete"></button>
        <a target="_blank" :href="href">
            <p><i :class="icon" :style="style"></i></p>
            
            <p>{{text}}</p>
        </a>
    </div>
</template>
        

<script>
export default {
    name: "Icon",
    props:{
        icon: String,
        animation: String,
        animatable: Boolean,
        text: String,
        href: String,
        color: {
            type: String,
            default: "#26454D"
        }
    },
    computed:{
        style (){
            return 'color: ' + (this.hovering ? this.color : this.color)
        }
    },
    methods:{
        async animate(){
            if (this.animatable){
                this.animating = !this.animating;
            }
            this.hovering = !this.hovering;
        },
    },
    data(){
        return{
            animating: false,
            text_concat: '',
            hovering: false
        }
    }
}

//    .grow:hover { transform: scale(1.05); background:#26454D; cursor: pointer; color:whitesmoke; }
</script>

<style scoped>

    .grow { min-height:75%; transition: all .08s ease-in-out;background:whitesmoke; margin-top:5% ; box-shadow: 0 0 0 1px #26454D inset}
    .grow:hover { transform: scale(1.05); cursor: pointer; filter:brightness(90%)}

    button {
        position: relative;
        left: 50%;
        right: 0;
        top: -10px;
        bottom: 0;
    }
</style>