<template>
    <div class="wrapper-popup" v-bind:class="getClassPopup">
       <div class="rule">
            <h3> Luật chơi </h3>
            <p>Minh Kiên has created the rule for dice game, so every players must observe this rule. If someone doesn't obey, we must kick you out of the game. please don't make me furious</p>
            <button
             v-on:click="confirm"
             class="confirm"> Tiếp tục </button>
       </div>
    </div>
</template>

<script>
    export default {
        name:'popup-rule',
        props:{
            isOpenPopup:{
                type:Boolean,
                default:false
            }
        },
        data(){
            return{

            }
        },
        methods:{
            confirm(){
                this.$emit('handleConfirm')
            }
        },
        computed:{
            getClassPopup(){
                return{
                    'open-popup':this.isOpenPopup
                }
            }
        }
    }
</script>

<style >
    .wrapper-popup{
        position: fixed;
        top:0;
        left:0;
        right: 0;
        bottom: 0;
        background-color: rgba(0, 0, 0, 0.4);
        opacity: 0;
        visibility: hidden;
        transition: all .5s ease;
    }
    .wrapper-popup.open-popup{
        opacity: 1;
        visibility: visible;
    }
    .rule{
        position: absolute;
        background-color: #fff;
        width: 400px;
        top: 50%;
        left: 50%;
        padding: 20px;
        font-family: Arial, Helvetica, sans-serif;
        transform: translate(-50%,-50%) scale(1.5);
        transition: all .5s ease;
    }
    .open-popup .rule{
        transform: translate(-50%,-50%) scale(1.2);
    }
    .rule h3{
        margin-bottom: 10px;

    }
    .rule .confirm{
        cursor: pointer;
        margin-top: 20px;
        padding: 8px 15px;
        border: 2px solid #333;
        background-color: #fff;
        transition: all .5s ease;
    }
    .rule .confirm:hover{
        color: #fff;
        background-color: #333;
    }
</style>