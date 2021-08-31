<template>
  <div>
    <form @submit.prevent="postdata()">
      <div style="width: 400px" class="mx-auto">
        <div class="form-group">
          <label for="exampleInputfname">First Name*</label>
          <input
            required
            type="text"
            class="form-control"
            id="exampleInputfname"
            aria-describedby="emailHelp"
            placeholder="Enter First Name"
            v-model="fname"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputmname">Middle Name</label>
          <input
            type="text"
            class="form-control"
            id="exampleInputmname"
            placeholder="Optional"
            v-model="mname"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputlname">Last Name*</label>
          <input
            required
            type="text"
            class="form-control"
            id="exampleInputlname"
            placeholder="Last Name"
            v-model="lname"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputdate">Date*</label>
          <input
            required
            type="date"
            class="form-control"
            id="exampleInputdate"
            placeholder="Last Name"
            v-model="date"
          />
        </div>
        <br />
        <div class="form-group">
          <label for="exampleInputgender">Gender*</label>&nbsp;&nbsp;
          <input
            type="radio"
            name="gender"
            value="male"
            v-model="gender"
            required
          />
          Male
          <input
            type="radio"
            name="gender"
            value="female"
            v-model="gender"
            required
          />
          Female
        </div>
        <div class="form-group">
          <label for="exampleInputmobno">Mobile Number*</label>
          <p>It should be of exact 10 digits</p>
          <input
            required
        
            class="form-control"
            id="exampleInputmobno"
            placeholder="Mobile No"
            v-model="mobile_no"
            type="text" maxlength="10"  pattern="[0-9]{10}"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputemail">Email</label>
          <input
            type="email"
            class="form-control"
            id="exampleInputemail"
            placeholder="Email"
            v-model="email"
          />
        </div>
        <br /><br />
        <div class="form-group">
          <p>Select graduation*</p>
          <select v-model="selected" required>
            <option disabled value="">Please select one</option>
            <option>Below 10th</option>
            <option>10th</option>
            <option>12th</option>
            <option>Graduation</option>
            <option>PG</option>
          </select>
        </div>
        <div class="form-group">
          <label for="exampleInputuname">Username*</label>
          <input
            required
            type="text"
            class="form-control"
            id="exampleInputuname"
            placeholder="Username"
            v-model="username"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputpassword">Password*</label>
          <p v-if="showdialog" style="color:red">Passwords didnt't match</p>
          <input
            required
            type="password"
            class="form-control"
            id="exampleInputpassword"
            placeholder="Password"
            v-model="password"
            minlength="8"
          />
        </div>
        <div class="form-group">
          <label for="exampleInputconfirmpassword">Confirm Password*</label>
          <input
            required
            type="password"
            class="form-control"
            id="exampleInputconfirmpassword"
            placeholder="Confirm Password"
            v-model="confirm_password"
            minlength="8"
          />
        </div>
        <br /><br />

        <button type="submit" class="btn btn-primary">Register</button>
        <hr />
        {{ fname }}
        {{ mname }}
        {{ lname }}
        {{ date }}
        {{ gender }}
        {{ mobile_no }}
        {{ email }}
        {{ selected }}
        {{ username }}
        {{ password }}
        {{ confirm_password }}
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "Register",
  data() {
    return {
      fname: "",
      mname: "",
      lname: "",
      date: "",
      gender: "",
      mobile_no: "",
      email: "",
      selected: "",
      username: "",
      password: "",
      confirm_password: "",
      showdialog: false,
    };
  },
  methods: {
    postdata() {
      if (this.password != this.confirm_password) {
        this.showdialog = true;
      } else {
          var register={
              fname:this.fname,
              mname:this.mname,
              lname:this.lname,
              dob:this.date,
              gender:this.gender,
              phone:this.mobile_no,
              email:this.email,
              education:this.selected,
              uname:this.username,
              pwd:this.password
          }
        axios.post("http://localhost:8080/auth/register",register)
        .then((res)=>{
            console.log(res.data)

        })
        .catch((e)=>{
            console.log(e)
        })
      }
    },
  },
};
</script>

<style>
</style>