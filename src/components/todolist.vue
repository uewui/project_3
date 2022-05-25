<template>
    <!-- 列表组 -->
    <ul class="list-group">
        <!-- 复选框 -->
        <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in todo" :key="item.id">
            <div class="form-check">
                <input class="form-check-input" type="checkbox" value="" id="item.id" v-model="item.done">
                <label class="form-check-label" for="item.id" :class="item.done?'delete':'' ">{{item.task}}</label>
            </div>
            <!-- 徽标 -->
            <span class="badge badge-success badge-pill" v-if="item.done">已完成</span>
            <span class="badge badge-warning badge-pill" v-else>未完成</span>
        </li>

    </ul>
</template>

<script>
export default {
    name: 'MyTodolist',
    props: {
        // 指定传递过来的数据的格式
        todo: {
            type:Array,
            require:true,
            fault:[]
        }
    }
}
</script>

<style lang="less" scoped>
// 修改列表宽度
.list-group {
    width: 300px;
}
// 删除效果
.delete {
    text-decoration: line-through ;
    color: grey;
    font-style: italic;
}
</style>