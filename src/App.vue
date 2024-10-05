<template>
  <div class="small-container">
    <h1>Employees</h1>
    <employee-form @add-employee="addEmployee"/>
    <employee-table 
    v-bind:employees="employees"
     @delete:employee="deleteEmployee"
     @edit:employee="editEmployee"
     />
    
  </div>

</template>

<script>
import EmployeeTable from './components/EmployeeTable.vue';
import EmployeeForm from './components/EmployeeForm.vue';
export default {
  name: 'App',
  components: {
    EmployeeTable,
    EmployeeForm
  },
  data(){
    return{
      employees:[
        {
          id:1,
          name:'sathish',
           email:'sathish017@gmail.com'
        },
        {
          id:2,
          name:'kumar',
           email:'kumar7@gmail.com'
        },
        {
          id:3,
          name:'naveen',
           email:'naveen017@gmail.com'
        }

      ]
    }
  },
  methods:{
    addEmployee(employee){
      
      const lastId = this.employees.length>0?this.employees[this.employees.length-1].id:0;

      const id = lastId + 1;

      const newEmployee ={...employee,id}

      this.employees=[...this.employees,newEmployee];

    },
    deleteEmployee(id){
            this.employees= this.employees.filter((employee)=>{
              return employee.id != id;
            })
    },
    editEmployee(id,updatedEmployee){
      this.employees.map((employee)=>{
        return employee.id==id?updatedEmployee:employee;
      })

    }
  }
}
</script>

<style>
button{
  background: #009435;
  border: 1px solid #009435;
}
.small-container{
  max-width: 700px;
}
</style>
