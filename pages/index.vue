<template>
<section>
  <div class ="py-4">
    <div class="container">
      <div class="title border-bottom d-flex align-item-center justify-content-between py-2">
        <h1>Tugas 3</h1>
        <div class="d-flex align-item-center">
          <span class="me-2">View As</span>
          <button
          class="btn btn-outline-secondary py-1 px-3"
          @click="isGrid=!isGrid">
          {{ isGrid?'Grid':'List' }}
          </button>
        </div>
      </div>
    </div>
  </div>
  <div class="list-task row">
    <div 
    :class="[
    'item-task d-flex align-items-start border-bottom pt-3 pb-4',
    isGrid? 'col-12 col-md-6 col-lg-4' :'col-12']">
<!-- // v-model berfungsi untuk mengikat variabel yang dideklarasikan dan secara
otomatis akan memperbaharui elemen berdasarkan tipe input -->
<input
id="task"
type="checkbox"
name="status"
class="me-2 mt-2"
:checked="tasks[0].isDone"
v-model="tasks[0].isDone"
>
<div
:class="['d-flex flex-column', tasks[0].isDone ?
'text-decoration-line-through fst-italic' : '']">
<div class="title-task mb-1">
{{ tasks[0].title }}
</div>
<div class="description-task small text-muted">
{{ tasks[0].description }}
</div>
</div>
</div>

<div 
    :class="[
    'item-task d-flex align-items-start border-bottom pt-3 pb-4',
    isGrid? 'col-12 col-md-6 col-lg-4' :'col-12']">
<!-- // v-model berfungsi untuk mengikat variabel yang dideklarasikan dan secara
otomatis akan memperbaharui elemen berdasarkan tipe input -->
<input
id="task"
type="checkbox"
name="status"
class="me-2 mt-2"
:checked="tasks[1].isDone"
v-model="tasks[1].isDone"
>
<div
:class="['d-flex flex-column', tasks[1].isDone ?
'text-decoration-line-through fst-italic' : '']">
<div class="title-task mb-1">
{{ tasks[0].title }}
</div>
<div class="description-task small text-muted">
{{ tasks[0].description }}
</div>
</div>
</div>

<div 
    :class="[
    'item-task d-flex align-items-start border-bottom pt-3 pb-4',
    isGrid? 'col-12 col-md-6 col-lg-4' :'col-12']">
<!-- // v-model berfungsi untuk mengikat variabel yang dideklarasikan dan secara
otomatis akan memperbaharui elemen berdasarkan tipe input -->
<input
id="task"
type="checkbox"
name="status"
class="me-2 mt-2"
:checked="tasks[2].isDone"
v-model="tasks[2].isDone"
>
<div
:class="['d-flex flex-column', tasks[2].isDone ?
'text-decoration-line-through fst-italic' : '']">
<div class="title-task mb-1">
{{ tasks[0].title }}
</div>
<div class="description-task small text-muted">
{{ tasks[0].description }}
</div>
</div>
</div>

</div>
</section>
</template>

<script>
export default{
data(){
  return{
    isGrid : false,
    isCreating : false,
    tasks : [
      {
        title :'Kelas X',
        description : 'Pembelajaran Kelas X',
        category : 'Tugas Harian',
        isDone :false,
      },
      {
        title :'Kelas XI',
        description : 'Pembelajaran Kelas XI',
        category : 'Tugas Harian',
        isDone :false,
      },
      {
        title :'Kelas XII',
        description : 'Pembelajaran Kelas XII',
        category : 'Tugas Harian',
        isDone :false,
      }
    ]
  }
}

}
</script>