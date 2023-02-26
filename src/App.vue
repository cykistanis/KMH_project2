<template>
  <div id="maindiv">
    <div class="container">
      <nav class="navbar navbar-expand-sm navbar-dark">
        <div class="container-fluid">
          <!-- Links -->
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link" href="#" @click="goallitems">All Items</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#" @click="gonewitems">Add New Items</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#" @click="goaboutus">About Us</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#" @click="gocontactus">Contact Us</a>
            </li>
          </ul>
        </div>
      </nav>
      <main>
        <Aboutus v-if="currentPage == 'aboutus'" />
        <Allitems v-if="currentPage == 'allitems'" @edit-items="goedititems" />
        <EditItems v-if="currentPage == 'edit-items'" />
        <Contactus v-if="currentPage == 'contactus'" />
        <AddNewItems
          v-if="currentPage == 'addnewitems'"
          @add-new-items="goallitems"
        />
      </main>
    </div>
  </div>
</template>

<script>
import Aboutus from "./components/Aboutus";
import Allitems from "./components/Allitems";
import Contactus from "./components/Contactus";
import AddNewItems from "./components/AddNewItems";
import EditItems from "./components/EditItems";

export default {
  name: "App",
  components: {
    Aboutus,
    Allitems,
    Contactus,
    AddNewItems,
    EditItems,
  },
  data: function () {
    return {
      currentPage: "allitems",
    };
  },
  methods: {
    goaboutus: function () {
      this.currentPage = "aboutus";
    },
    goallitems: function () {
      this.currentPage = "allitems";
    },
    gocontactus: function () {
      this.currentPage = "contactus";
    },
    gonewitems: function () {
      this.currentPage = "addnewitems";
    },
    goedititems: function (itemId) {
      this.currentPage = "edit-items";
    },
  },
};
</script>

<style>
#maindiv {
  background-color: #f5f5f5;
  font-family: "Helvetica Neue", sans-serif;
  font-size: 16px;
  line-height: 1.5;
  margin: 0;
  padding: 0;
}

.navbar {
  background-color: rgb(113, 151, 148);
  border-radius: ;
}

.navbar-brand {
  font-weight: bold;
}

.navbar-nav .nav-link {
  color: #fff;
  font-weight: bold;
  padding: 0.5rem 1rem;
  text-transform: uppercase;
  transition: all 0.2s ease-in-out;
}

.navbar-nav .nav-link:hover {
  background-color: rgb(127, 202, 137);
  border-radius: 5px;
}

main {
  margin: 1rem;
  padding: 1rem;
}
</style>
