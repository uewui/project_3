<template>
    <div class=" button-container mt-3">
        <div class="btn-group" role="group" aria-label="Basic example">
            <button type="button" class="btn" :class="active===0?'btn-primary':'btn-secondary' " @click="onBtnClick(0)">全部</button>
            <button type="button" class="btn" :class="active===1?'btn-primary':'btn-secondary'"  @click="onBtnClick(1)" >已完成</button>
            <button type="button" class="btn" :class="active===2?'btn-primary':'btn-secondary'"  @click="onBtnClick(2)">未完成</button>
        </div>
    </div>

</template>

<script>
export default {
    name: 'TodoButton',
    props: {
        // 激活项的索引值
        active: {
            type:Number,
            require:true,
            // 默认索引为0
            default:0,
        }
    },
    emits:['update:active'],
    methods: {
        onBtnClick(index) {
            if(index===this.active) return
            this.$emit('update:active',index)
        }
    }
   
}
</script>

<style lang="less" scoped>
.button-container {
    text-align: left;
}
</style>