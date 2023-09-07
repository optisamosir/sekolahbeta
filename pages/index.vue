<template>
<section>
  <div class="title border-bottom d-flex align-items-center py-2">
    <h5>Task</h5>
    <div class="d-flex align-items-center ms-auto">
      Pilih Semester
      <div class="d-flex align-items-center justify-content-end w-100">
        <select class="form-select" v-model="selectedCategory" placeholder="Pilih Semester">
          
          <option value="1">Semester 1</option>
          <option value="2">Semester 2</option>
        </select>    </div>
  </div>
</div>
<div class="list-task row">
  <CardItem
  v-for="(task, i) in resultQuery"
  :key="i"
  :task="task"
  :isGrid="isGrid"
  />
</div>
</section>
</template>

<script>
import CardItem from "@/components/Card/CardItem.vue"
export default {
  components: {
    CardItem
  },
  data(){
  return{
    selectedCategory:'',
    searchQuery: '',
    isCreating: false,
    isGrid: false,
    tasks : [
      {
        title :'Kelas X',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'Kelas X',
        description : 'Ulangan',
        category : 'Semester 2',
        isDone :false,
      },
      {
        title :'Kelas XI',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'Kelas XI',
        description : 'Ulangan',
        category : 'Semester 2',
        isDone :false,
      },
      {
        title :'Kelas XII',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'Kelas XII',
        description : 'Ulangan',
        category : 'Semester 2',
        isDone :false,
      }
    ]
  }
},
computed :  {
    resultQuery() {
      if (!this.selectedCategory) {
        return this.tasks;
      } else {
        return this.tasks.filter((item)=> {
          return item.category.includes(this.selectedCategory);
        });
      }
}
}
}
</script>