<template>
  <div>
    <h1>
      Romantic Restaurant Reviews
    </h1>

    <h2>
      About Us
    </h2>

    <nav>
      <ul>
        <li><a href="/about-us">About Us</a></li>
        <li><a href="/restaurant-list">Restaurant List</a></li>
        <li><a href="/reviews">Reviews</a></li>
      </ul>
    </nav>

    <input type="text" :value="geoPosition">
    
    <button @click="searchCity">Add</button>
    <button @click="logout">Logout</button>
    <button @click="deleteUser">Delete my Account...</button>
     
    <div>
      <h3>Our Mission Statement</h3>
      <p><i>Romantic Restaurant Reviews</i> helps couples find romantic spots to dine.</p>
      <h3>The Purpose</h3>
      <p>
        <i>Romantic Restaurant Reviews</i> is a web application designed to educate users of nearby restaurants that provide a romantic ambiance. We have collected data from local restaurant reviews, and have selected the top restaurants based on qualities such as lighting, food, decor, and more.
      </p>
    </div>
  </div>
</template>

<script lang="ts">
// import ChildComponent from "./60-props-child.vue";
import axios, { AxiosResponse } from "axios";
//import {DocumentReference, CollectionReference,  addDoc, collection} from “firebase/firestore";
import { getAuth, deleteUser, signOut } from "firebase/auth";
import { Vue, Component } from "vue-property-decorator";
import { ZoneRegion } from "@js-joda/core";

@Component
export default class TestOneView extends Vue {

 // Save Data Function
 logout(): void {
   const auth = getAuth();
   const user = auth.currentUser;
   signOut(auth)
   this.$router.back();
 }

 // DELETE USER FUNCTION
deleteUser(): void {
    const auth = getAuth();
    const user = auth.currentUser;

  if (user !== null) {
    deleteUser(user)
    
    .then(() => {
      this.$router.push("/");
     
  // User deleted.
}).catch((error) => {
  // An error ocurred
  // ...
});
  
  }}
  
}

</script>

<style scoped>
h1 {
  text-align: center;
  color: red;
  font-size: 60px;
  font-family:cursive;
}

h2 {
  font-family:Georgia, 'Times New Roman', Times, serif;
  text-align: center;
}

p {
    background-color:rgb(235, 212, 232);

}

nav {
    /* height: 40px; */
    margin-bottom: 10px;
    margin-top: 10px;
    text-align: center;
    background: #f7c1cb;
}

nav ul {
    margin-left: auto;
    margin-right: auto;
}

nav li {
    display: inline-block;
    height: 100%;
    width: 20%;
}

nav li a {
    font-family: cursive;
    color: #ff1e4b;
    font-size: 20px;
    text-decoration: none;
}

nav li a:hover {
    color: #dd5771;
}

pre {
  white-space: normal;
  padding: 0.5em;
  border: 2px solid gray;
}

</style>