<script>
    export default{
        props: {
            item: {
                type: Object,
                required: true
            },
            index:{
                type: Number,
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
    <div className="item" >
        Id: <b>{{ item.id }}</b><br/>Name:<br/><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ item.name }}</b>
        <div className="button">
            <button @click="actionItem(index, item.id)">{{ actionText }}</button>
        </div>
        
    </div>
</template>

<style scoped>
.item{
    display: block;
    width: 120px;
    height: 120px;
    border: 5px solid #ccc;
    padding: 5px;
    margin: 5px;
    text-align: left;

    & .button{
        margin-top: 20px;
        text-align: center;
    }
}
</style>