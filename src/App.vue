<script>
import LeftTopSide from './components/LeftTopSide.vue'
import RightTopSide from './components/RightTopSide.vue'
import LeftBottomSide from './components/LeftBottomSide.vue'
import RightBottomSide from './components/RightBottomSide.vue'

export default{
  components: { LeftTopSide, RightTopSide, LeftBottomSide, RightBottomSide },
  data(){
    return {
      addText: 'Click to add',
      deleteText: 'Click to delete',
      leftTopArray: [],
      rightTopArray: [],
      leftBottomArray: [
        {"id": 1, "name": "Shoes 1"},
        {"id": 2, "name": "Shoes 2"},
        {"id": 3, "name": "Shoes 3"},
        {"id": 4, "name": "Shoes 4"},
        {"id": 5, "name": "T-shirt 1"},
        {"id": 6, "name": "T-shirt 2"},
        {"id": 7, "name": "T-shirt 3"},
        {"id": 8, "name": "T-shirt 4"}
      ],
      rightBottomArray: [
        {"id": 11, "name": "Jacket 1"},
        {"id": 12, "name": "Jacket 2"},
        {"id": 13, "name": "Jacket 3"},
        {"id": 14, "name": "Jacket 4"},
        {"id": 15, "name": "Hoodie 1"},
        {"id": 16, "name": "Hoodie 2"},
        {"id": 17, "name": "Hoodie 3"},
        {"id": 18, "name": "Hoodie 4"}
      ]
    }
  },
  methods:{
    addLeftData(index, id){
      let item_from = this.leftBottomArray.find((item)=>{
        return item.id === id;
      })
      let item_to = this.leftTopArray.find((item)=>{
        return item.id === id;
      })
      if(this.leftTopArray.length < 6 && item_from && !item_to) this.leftTopArray.push(item_from);

    },
    addRightData(index, id){
      let item_from = this.rightBottomArray.find((item)=>{
        return item.id === id;
      })
      let item_to = this.rightTopArray.find((item)=>{
        return item.id === id;
      })
      if(item_from && !item_to) this.rightTopArray[0] = item_from;
    },

    deleteFromLeft(index, id){
      let item_to = this.leftTopArray.find((item)=>{
        return item.id === id;
      })
      if(item_to) this.leftTopArray.splice(index, 1);
    },
    deleteFromRight(index, id){
      this.rightTopArray = [];
    }
  }

}
</script>

<template>
    <LeftTopSide :items="leftTopArray" :actionItem="deleteFromLeft" :actionText="deleteText"/>
    <RightTopSide :items="rightTopArray" :actionItem="deleteFromRight" :actionText="deleteText"/>
    <div className="br"></div>
    <LeftBottomSide :items="leftBottomArray" :actionItem="addLeftData" :actionText="addText"/>
    <RightBottomSide :items="rightBottomArray" :actionItem="addRightData" :actionText="addText"/>
</template>

<style lang="scss" scoped>
.br{
  display: table-row;
}
</style>
