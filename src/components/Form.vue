<template>
  <div>
    <div class="form-container" id="login-form">
      <form action="#" method="POST">
        <h1 class="form-header">Welcome!</h1>

        <!-- <InputField
          type="text"
          placeholder="Username"
          icon="user"
          iconColor="blueviolet"
          :inputData="formData.username"
        /> -->
        <div class="input" id="username-input">
          <fa class="icon" icon="user" />
          <input
            type="text"
            placeholder="Username"
            v-model="formData.username"
          />
        </div>
        <InputField
          type="password"
          placeholder="Password"
          icon="key"
          iconColor="blueviolet"
        />
        <Button text="Log In" type="submit" />
        <input type="hidden" value="login" />
        <p>
          You don't have an account?
          <a href="#" v-on:click="toggleForm" class="form-link">Register now</a
          >.
        </p>
      </form>
    </div>
    <div class="form-container" id="register-form" style="display: none">
      <form action="#" method="POST">
        <h1 class="form-header">Welcome!</h1>

        <InputField
          type="text"
          placeholder="Username"
          icon="user"
          iconColor="blueviolet"
        />
        <InputField
          type="text"
          placeholder="Email"
          icon="key"
          iconColor="blueviolet"
        />
        <InputField
          type="password"
          placeholder="Password"
          icon="key"
          iconColor="blueviolet"
        />
        <InputField
          type="password"
          placeholder="Repeat Password"
          icon="key"
          iconColor="blueviolet"
        />
        <input type="hidden" value="register" />
        <Button text="Sign Up" type="submit" />
        <p>
          You already have an account?
          <a href="#" v-on:click="toggleForm" class="form-link">Log in</a>.
        </p>
      </form>
    </div>
  </div>
</template>
<script>
import InputField from "./InputField.vue";
import Button from "./Button.vue";

var formToggler = false;

export default {
  name: "Form",
  components: {
    InputField,
    Button,
  },
  methods: {
    toggleForm() {
      formToggler = !formToggler;
      var loginFormElement = document.getElementById("login-form");
      var registerFormElement = document.getElementById("register-form");
      if (!formToggler) {
        // we need to change from register form to log in form
        loginFormElement.style = "display: flex;";
        registerFormElement.style = "display: none;";
      } else {
        // we need to change from log in form to register form
        loginFormElement.style = "display: none;";
        registerFormElement.style = "display: flex;";
      }
    },
  },
  data() {
    return {
      formData: {
        username: "",
        email: "",
        password: "",
        repeatPassword: "",
        formType: "",
      },
    };
  },
};
</script>

<style scoped>
.form-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

form {
  display: flex;
  flex-direction: column;
  width: 30%;
  min-width: max-content;
  height: 100%;
  justify-content: center;
  align-items: center;
  background: white;
  color: var(--primary-clr);
  border-radius: 1rem;
  padding: 2rem 1rem;
  box-shadow: 0 0.1rem 1rem 0.2rem rgba(126, 126, 126, 0.3);
}

p {
  color: black;
}
a {
  text-decoration: none;
}
.form-link {
  color: var(--primary-clr);
  transition: 0.5s;
}
.form-link:hover,
.form-link:focus {
  color: var(--dark-clr);
}

.input {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}
.input > input {
  height: 2rem;
  background: white;
  color: var(--dark-clr);
  border-radius: 2rem;
  padding: 0.2rem 1rem;
  margin: 0.2rem;
  border: none;
  box-shadow: 0 0rem 0rem 0.1rem rgba(0, 0, 0, 0.1);
  font-weight: bold;
  transition: 0.5s;
}

.input > input::placeholder {
  color: var(--mid-dark-clr);
}

.input > input:focus {
  border: none;
  box-shadow: 0 0.1rem 1rem 0.2rem rgba(0, 0, 0, 0.3);
}

.input > .icon {
  /* color: var(--icon-color); */
  color: var(--primary-clr);
  margin: 0 0.5rem;
}
</style>
