<template>
    <form class="form-inline" @submit.prevent="add">
        <div class="form-group mx-sm-3 mb-2">
            <!-- 输入框的前缀 -->
            <div class="input-group-prepend">
                <div class="input-group-text">任务</div>
            </div>
            <!-- 文本输入框 -->
            <input type="text" class="form-control" placeholder="请输入任务信息" v-model.trim="taskname">
        </div>
        <!-- 添加按钮 -->
        <button type="submit" class="btn btn-primary mb-2">添加任务</button>
    </form>
</template>

<script>
export default {
    name: 'TodoInput',
    data() {
        return {
            taskname: ''
        }
    },
    emits: ['addtask'],
    methods: {
        add() {
            if (!this.taskname) return alert('任务名称不能为空')
            this.$emit('addtask', this.taskname)
            this.taskname=''

        }
    }

}
</script>

<style lang="less" scoped>
</style>