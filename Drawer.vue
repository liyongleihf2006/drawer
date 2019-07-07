<template>
    <div v-if="mask" class="drawer" :class="{'drawer-show':show}">
        <div 
            class="drawer-panel" 
            :class="{'drawer-open':open}"
            @transitionend="transitionend"
        >
            <slot></slot>
        </div>
    </div>
    <div 
        v-else
        class="drawer-panel drawer-no-mask-panel" 
        :class="{'drawer-open':open}"
        @transitionend="transitionend"
    >
        <slot></slot>
    </div>
</template>

<script>
export default {
    props:{
        open:{
            required:true,
            type:Boolean
        },
        mask:{
            type:Boolean,
            default:true
        }
    },
    data(){
        return {
            show:false
        }
    },
    watch:{
        open (val) {
            if(val){
                this.show = true;
            }
        }
    },
    methods:{
        transitionend(){
            if(!this.open){
                this.show = false;
            }
        }
    }
}
</script>

<style>
    .drawer{
        visibility: hidden;
        position: fixed;
        top:0;
        bottom:0;
        left:0;
        right:0;
        background-color: rgba(0,0,0,0.1);
    }
    .drawer-panel{
        width: max-content;
        height:100%;
        margin-left:auto;
        background:#fff;
        transition: transform .3s;
        transform: translateX(100%);
    }
    .drawer-no-mask-panel{
        position: fixed;
        top:0;
        right:0;
    }
    .drawer-show{
        visibility:visible;
    }
    .drawer-panel.drawer-open{
        transform: translateX(0);
    }
</style>
