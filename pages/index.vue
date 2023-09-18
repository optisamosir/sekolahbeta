<template>

<!-- Card -->
<div class="py-4">
  <div class="container">
  <div class="title border-bottom d-flex align-items-center justify-content-between py-2">
    <h5>Task</h5>
    <div class="d-flex align-items-center">
      <select v-model="selectedCategory" class="form-select" >  
              <option value="1">Semester 1</option>
              <option value="2">Semester 2</option>
      </select>    
      <div class="d-flex align-item-center justify-content-end w-100">
      <span class="me-2">View As</span>
      <button
      class="btn btn-outline-secondary py-1 px-3"
      @click="isGrid=!isGrid" >
      {{ isGrid ? 'Grid' : 'List' }}
      </button>
    </div>
    </div>
  </div>
  <div class="action py-2">
    <a
      v-if="!isCreating" href="#" class="add-button"
      @click="isCreating=!isCreating">Add Task</a>
    <div v-else class="add-card">
      <form v-on:submit.prevent="handleSubmit">
        <div class="field">
            <label class="label">Input Kelas</label>
            <div class="control">
                <input v-model="form.title" class="input" type="text"
                 placeholder="X/XI/XII">
            </div>
            <label class="label">Jenis Tugas</label>
            <div class="control">
                <input v-model="form.description" class="input" type="text"
                 placeholder="Masukkan Jenis Tugas">
            </div>

            <label class="label">Pilih Semester</label>
            <div class="control">
                <select v-model="form.category">
                <option v-for="option in options.inquiry" v-bind:key="option.value">
                {{ option.text }}</option>
            </select>
            </div>
        </div>
        <div class="button-wrapper d-flex">
          <button class="btn btn-primary me-2">Save</button>
          <button
          class="btn btn-outline-secondary"
          @click="isCreating =!isCreating">Cancel</button>
        </div>
      </form>
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
  </div>
  </div>
</template>

<script>
import CardItem from "@/components/Card/CardItem.vue"
export default {
  methods: {
            handleSubmit() {
                // console.log(this.form)
                const item = {
                    form: this.form
                }
                this.tasks.push(item)
            }
          },
  components: {
    CardItem
  },
  data(){
  return{
    form : {
      name: ''
    },
    options: {
                    inquiry: [
                        { value: 'Semester 1', text: "Semester 1"},
                        { value: 'Semester 2', text: "Semester 2"}
                    ]
                },
    selectedCategory:'',
    searchQuery: '',
    isCreating: false,
    isGrid: false,
    tasks : [
      {
        title :'X',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'X',
        description : 'Ulangan',
        category : 'Semester 2',
        isDone :false,
      },
      {
        title :'XI',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'XI',
        description : 'Ulangan',
        category : 'Semester 2',
        isDone :false,
      },
      {
        title :'XII',
        description : 'Ulangan',
        category : 'Semester 1',
        isDone :false,
      },
      {
        title :'XII',
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
<style>
</style>