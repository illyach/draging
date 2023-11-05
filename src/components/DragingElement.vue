<template>
    <div>
        <div
        ref="draggableDiv"
      class="draggable-div"
      :style="dynamicStyles"
      @mousedown="startDrag" 
      @mousemove="drag"
      @mouseup="stopDrag"
      @mouseleave="stopDrag"
        >
        drag and drop me
        </div>
    </div>
</template>

     
   
<script>
export default {
  data() {
    return {
      dynamicStyles: {
        position: "absolute",
        left: "680px",
        top: "300px",
        backgroundColor: "lightgreen",
        width: "100px",
        height: "100px",
        border: "2px solid black"
      },
      
      isDragging: false,
      offsetX: 0,
      offsetY: 0
  }
},
methods:{
    startDrag(e){
        this.isDragging = true;
        const rect = this.$refs.draggableDiv.getBoundingClientRect();
        this.offsetX = e.clientX - rect.left;
        console.log(this.offsetX, this.offsetY)
        this.offsetY = e.clientY - rect.top;
    },
      drag(e) {
      if (this.isDragging) {
        this.dynamicStyles.left = e.clientX - this.offsetX + "px";
        this.dynamicStyles.top = e.clientY - this.offsetY + "px";
      }
    },
    stopDrag() {
      this.isDragging = false;
    },
}

}
</script>

