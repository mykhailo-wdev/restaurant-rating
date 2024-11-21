<template>
    <div class="row" v-if="isHeader">
        <h4 class="header">Rank</h4>
        <h4 class="header">Chain</h4>
    </div>
    
    <div v-else class="row" :class="{'highlight-row': isEven(index)}">
        <h4 class="header rank">{{ rank }}</h4>
        <a :href="`/restaurants/${name}`" class="header link">{{ name }}</a>
    </div>
</template>

<script setup lang="ts">
interface RowProps {
    rank?: number;    
    name?: string;   
    index?: number;   
    isHeader?: boolean; 
}


const props = defineProps<RowProps>()


const isEven = (index: number = 0): boolean => {
  return index % 2 === 0;
}
</script>

<style scoped>

.row {
  border-top: 1px solid rgba(128, 128, 128, 0.336);
  display: flex;
  align-items: center;
}

.header {
  font-size: 1.25rem;
  color: rgb(10, 31, 148);
  margin: 0;
  margin-right: 2rem;
  padding: 0.5rem 1rem;
  font-weight: 700;
  width: 4rem;
}


.rank {
  color: black;
}

.link {
  text-decoration: none;
  color: rgb(228, 157, 27);
  width: auto;
  font-weight: 500;
}

.highlight-row {
  background-color: rgba(128, 128, 128, 0.15);
}
</style>
