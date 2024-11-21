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
    <div className="right-bottom">
        <div>
            <Item v-for="(el, index) in items" :key="index" :item="el" :index="index" :actionItem="actionItem" :actionText="actionText"/>
        </div>
    </div>
</template>

<style scoped>
.right-bottom{
    display: table-cell;
    width: 50%;
    text-align: right;
    vertical-align: top;

    & > div{
        display: flex;
        flex-wrap: wrap;
        align-content: flex-start;
        width: 100%;
        height: 70vh;
        border: 5px solid #ccc;
        padding: 5px;

    }
}
</style>