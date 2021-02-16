<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>email: </label>
      <input type="email" required v-model="email" />

      <label>password: </label>
      <input type="password" required v-model="password" />
      <div class="error" v-if="passwordError">
        {{ passwordError }}
      </div>

      <label>Role: </label>
      <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="designer">Web Designer</option>
      </select>

      <label>Skills: </label>
      <input type="text" v-model="tempSkills" @keyup="addskills" />
      <div class="pills" v-for="skill in skills" :key="skill">
        <span @click="deleteSkill(skill)"> {{ skill }} </span>
      </div>
      <div class="terms">
        <input type="checkbox" required v-model="terms" />
        <label> Accept terms and conditions</label>
      </div>
      <div class="submit">
        <button>Create Account</button>
      </div>
    </form>
    <p>
      Email: {{ email }}<br />
      Password: {{ password }} <br />
      Role: {{ role }} <br />
      Terms Accepted: {{ terms }}
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "designer",
      terms: false,
      tempSkills: "",
      skills: [],
      passwordError: ""
    };
  },
  methods: {
    addskills(e) {
      if (e.key === "Enter" && this.tempSkills) {
        if (!this.skills.includes(this.tempSkills)) {
          this.skills.push(this.tempSkills);
        }
        this.tempSkills = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter(item => {
        return skill !== item;
      });
    },
    handleSubmit() {
      //vaalidate password
      this.passwordError =
        this.password > 6 ? "" : "Password must be 6 characters long";
    }
  }
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: #0c0c0f;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
  opacity: 0.9;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  letter-spacing: 1px;
  font-weight: bold;
  text-transform: uppercase;
}
input,
select {
  display: block;
  padding: 15px 6px;
  width: 100%;
  border: none;
  box-sizing: border-box;
  color: white;
  background: #18181b;
  border: none;
  border-radius: 20px;
}
input[type="checkbox"] {
  width: 16px;
  display: inline-block;
  position: relative;
  margin: 0 0 16px 0;
  top: 2px;
}
.pills {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #777;
  cursor: pointer;
}
button {
  padding: 10px 20px;
  background: cornflowerblue;
  border: none;
  border-radius: 20px;
  color: white;
  margin-top: 20px;
}
.submit {
  text-align: center;
}
.error {
  color: crimson;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
