<script lang="ts">
import { initializeApp } from "firebase/app";
import { getAuth, createUserWithEmailAndPassword} from "firebase/auth"

let email: string
let password: string

const firebaseConfig = {
  apiKey: "AIzaSyC-zLiUghEu93CroQ8Vfl2ahFIzRHQBc1k",
  authDomain: "my-musik-a33e9.firebaseapp.com",
  projectId: "my-musik-a33e9",
  storageBucket: "my-musik-a33e9.appspot.com",
  messagingSenderId: "454758068992",
  appId: "1:454758068992:web:9193911c60cd7e8edf79e5"
};

const app = initializeApp(firebaseConfig);

const handleOnSubmit = () => {
  const auth = getAuth();
  createUserWithEmailAndPassword(auth, email, password)
    .then((userCredential) => {
      const user = userCredential.user;
      console.log({user})
    })
    .catch((error) => {
      console.log({error})
      const errorCode = error.code;
      const errorMessage = error.message;
    });
}

</script>


<div class="flex justify-center items-center h-full">
  <div class="bg-glass p-8 w-1/3">
    <form 
      class="flex flex-col gap-y-16" 
      on:submit={handleOnSubmit}
    >
      <div class="flex flex-col">
        <label for="email">email</label>
        <input 
          class="p-2" 
          type="email"
          id="email" 
          name="email" 
          placeholder="Enter your email" 
          required
          bind:value={email}
        >
      </div>
  
      <div class="flex flex-col">
        <label for="password">Password</label>
        <input 
          class="p-2" 
          type="password"
          minlength="6"
          id="password"
          name="password" 
          placeholder="Enter your password" 
          required
          bind:value={password}
        >
      </div>
  
      <input type="submit" value="Login">
    </form>
  </div>
</div>