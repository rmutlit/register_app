<template>
  <v-container>
  <v-form
    ref="form" v-model="valid" lazy-validation>
    <div class="Registers">
    <div>
      <br> 
      <h1>กรอกข้อมูลการสมัครสมาชิก</h1>
    </div>

  </div>
    <v-row>
      <v-col cols="4">
    <v-text-field
      v-model="firstname"
      :rules="firstnameRules"
      label="ชื่อ"
      required
    ></v-text-field>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="4">
    <v-text-field
      v-model="lastname"
      :rules="lastnameRules"
      label="นามสกุล"
      required
    ></v-text-field>
      </v-col>
    </v-row>

    <v-btn
      :disabled="!valid"
      rounded
      color="success"
      class="mr-4"
      @click="validate"
    >
      สมัครสมาชิก
    </v-btn>

  </v-form>
  </v-container>
</template>


<script>
import axios from "axios";

export default {data: () => ({
    valid: false,
    firstname: "",
    firstnameRules: [
      v => !!v || "" ],
    lastname: "",
    lastnameRules: [
      v => !!v || "" ],
      
      desserts: []
    }),
    methods: {
      validate() {
      if (this.$refs.form.validate()) {
        axios.post("http://localhost:3000/api/registers", {
            "firstname":`${this.firstname}`,
            "lastname":`${this.lastname}`
            }).then((res) => {
            console.log(res)
        });
      }
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    }
  }
};
</script>

<style>
</style>