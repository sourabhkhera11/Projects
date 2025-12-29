<script lang="ts">
    import { defineComponent } from 'vue';
    export default defineComponent({
        props:{
            flag:String,
            cname:String,
        }
    })
</script>
<template>
        <div class="box">
            <div class="flag">
                {{ flag }}
            </div>
            <div class="country">
                {{ cname }}
            </div>
        </div>
</template>
<style scoped>
    .box{
        height: 250px;
        width: 250px;
        display: flex;
        gap: 40px;
        justify-content: center;
        align-items: center;
    }
    .flag,.country{
        font-size: 30px;
        text-align: center;
    }
</style>