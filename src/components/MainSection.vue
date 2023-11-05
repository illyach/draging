<template>
  <div>
    <h1>Museum info</h1>
    <p :style="dynamicStyles">
      Delightful unreserved impossible
      ew estimating men favourable see entre
      aties. She propriety <br />immediate was improvi
      ng. He or entrance humoured likewise moderat
      e. Much nor game son say feel.
      <br /> Fat make met can
      must form into gate. Me we offending prevailed discovery.
    </p>
    <TextSection v-show="isOpen" />
    <button @click="doTogether">More details</button>
  </div>


  <div>
    <DragingElement/>
  </div>
</template>

<script setup>
import TextSection from './TextSection.vue';
import DragingElement from './DragingElement.vue';


import { ref } from 'vue';

const isOpen = ref(false);
const dynamicStyles = ref({
  backgroundColor: 'red',
  color: 'white',
  fontSize: '16px',
});



const changeStyles = () => {

  dynamicStyles.value.backgroundColor = (dynamicStyles.value.backgroundColor === 'blue' ? 'red' : 'blue');
  dynamicStyles.value.color = (dynamicStyles.value.backgroundColor === 'blue' ? 'white' : 'white');
  dynamicStyles.value.fontSize = (dynamicStyles.value.backgroundColor === 'blue' ? '16px' : '16px');
 
};

const doTogether = () => {
  toggleTextSection();
  changeStyles();
};

const toggleTextSection = () => {
  isOpen.value = !isOpen.value;
};
</script>
