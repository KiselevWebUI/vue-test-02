<script>
import Item from './Item.vue'

export default{
    components: { Item },
    props: {
        items: {
            type: Array,
            required: true
        },
        actionText:{
            type: Text,
            required: true
        },
        actionItem:{
            type: Function,
            required: true
        }
    }
}
</script>

<template>
    <div className="right-top">
        <div aligh="right">
            <Item v-for="(el, index) in items" :key="index" :item="el" :index="index" :actionItem="actionItem" :actionText="actionText"/>
        </div>
    </div>
</template>

<style scoped>
.right-top{
    display: table-cell;
    width: 50%;
    text-align: right;
    vertical-align: top;
    
    & > div{
        display: table;
        border: 5px solid #ccc;
        width: 100%;
        padding: 5px;
        height: 100%;
    }
}
</style>