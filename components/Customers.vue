<template>
    
    <div id="app" color="blue">
      <div class="container">
        <div>
  <b-button v-b-modal.modal-1>Add Customers</b-button>

  <b-modal id="modal-1" hide-footer title="Add Customers">
    <p class="my-4"></p>
    <br>
        <div class="form-inline" action="#">
        <input type="text" id="form-name" v-model="item.name" placeholder="Name" class="form-control"> 
        <input type="text" v-model="item.desc" placeholder="Description" class="form-control" v-on:keyup.enter="addItem">
        
    
  </div>
  <div class="modal-footer">
    <button @click="addItem" class="btn btn-dark"><i class="fas fa-plus">+</i></button>
  </div>
  
  </b-modal>
  
</div>
        
         
          
        <br><br>
        <table class="table table-striped table-bordered table-sm">
          <thead class="thead-light">
            <th>Name</th>
            <th>Description</th>
            <th class="col-2">Edit/Del</th>
          </thead>
          <tr v-for="(item, index) in items">
            <td>
              <input v-if="item.edit" type="text" v-model="item.name"  v-on:keyup.enter="item.edit = !item.edit">
              <span v-else>{{item.name}} </span>
            </td>
            <td>
              <input v-if="item.edit" type="text" v-model="item.desc" v-on:keyup.enter="item.edit = !item.edit">
              <span v-else>{{item.desc}} </span>
            </td>
            <td><button @click="item.edit = !item.edit" class="btn btn-info"><i class="far fa-edit">Edit</i></button>
              <button @click="removeItem(index)" class="btn btn-danger"><i class="far fa-trash-alt">Delete</i></button></td>
          </tr>
        </table>
      </div>
    </div>
    </template>
    
    <script>
    export default({
      data: function() {
        return {
          item: {name: "", desc: "", edit: false},
          items: []
        }
      },
      methods:{
        addItem(){
          this.items.push({name:this.item.name, desc:this.item.desc, edit: false})
          this.item = [];
         // $('#form-name').focus();
        },
        removeItem(index){
          this.items.splice(index, 1)
        }
      }
    });


    
    </script>
    
    <style>
    .form-inline input {
      margin-right:8px;
    }
    </style>