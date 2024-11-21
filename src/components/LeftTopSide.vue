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
    <div className="left-top">
        <div>
            <Item v-for="(el, index) in items" :key="index" :item="el" :index="index" :actionItem="actionItem" :actionText="actionText"/>
        </div>
    </div>
</template>

<style scoped>
.left-top{
    display: table-cell;
    width: 50%;
    height: 18.5%;
    vertical-align: top;
    
    & > div{
        display: flex;
        flex-wrap: wrap;
        align-content: flex-start;
        border: 5px solid #ccc;
        width: 100%;
        height: 100%;
        padding: 5px;
    }
}
</style>