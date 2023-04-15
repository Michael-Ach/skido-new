<template>
  <v-container class="">
    <div class="justForFun">Enjoy Skidooooooooo</div>
    <template>
      <v-card class="p-64">
        <v-data-table
          ref="myTable"
          :headers="headers"
          :items="soul"
          :items-per-page="10"
          class="elevation-1"
        >
        </v-data-table>
      </v-card>
    </template>
  </v-container>
</template>

<script>
import newRequest from '@/utils/newRequest';
export default {
  name: "HomeView",

  data() {
    return {
      soul: [],
      headers: [
        {
          text: "Name",
          value: "name",
        },

        {
          text: "Contact",
          value: "contact",
        },
        {
          text: "Gender",
          value: "gender",
        },
        {
          text: "Town",
          value: "town",
        },
      ],
      loading: false,
    };
  },

  methods:{
    getSouls() {  
      this.loading = true;  
      newRequest.get("/souls").then((res) => {  
         
          console.log(res);
          this.soul = [...res.data.data];
        });  
    },  
  },

  mounted() {
    this.getSouls();
  }
};
</script>


<style scoped>
.justForFun {
  display: flex;
  justify-content: center;
  font-size: 30px;
  margin-bottom: 20px;
  font-weight: bolder;
  color: red;
}
</style>