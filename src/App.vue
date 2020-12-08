<template>
  <div id="app" data-spy="scroll" data-target="#navigation" data-offset="50">
    <section class="mb-5">
      <div class="container">
        <h1 class = "display-3 bold mb-3"> Storing Data Locally </h1>
        <p> In this lesson, you will learn how apps store data on devices like phones and computers. Then, you'll apply what you've learned by working with a to-do list in App Inventor or Thunkable! </p>
        <b-nav>
            <SectionNav iconName="patch-question-fll" title="Learn" description="Storing Information On Your Device"/>
            <SectionNav iconName="list-stars" title="Activity" description="To-Do List"/>
            <SectionNav iconName="search" title="Reflection" description="Apply What You've Learned!" v-b-visible="activateSideNav"/>
          <div class="side-nav" :style="{opacity: sideNavVisible ? '100%' : '0%'}" v-b-scrollspy:nav-scroller>
            <b-nav-item href="#Learn"><b-icon class="side-nav-icon" icon="patch-question-fll" font-scale="1"/></b-nav-item>
            <b-nav-item href="#Activity"><b-icon class="side-nav-icon" icon="list-stars" font-scale="1"/></b-nav-item>
            <b-nav-item href="#Reflection"><b-icon class="side-nav-icon" icon="search" font-scale="1"/></b-nav-item>
          </div>
        </b-nav>
        <h3 class="mb-3 text-muted"> Key Terms </h3>
        <p class="text-muted"> Click to see definitions </p>
        <b-row class="row-cols-1 row-cols-md-3">
          <KeyTerm v-for="term in keyTerms" v-bind:key="term.iconName" v-bind:term="term"/>
        </b-row>
      </div>
    </section>
    <section id="Learn" class="mb-5">
      <div class="container">
        <h2>Storing Information on Your Device</h2>
        <p>
          When we store information on our phones and computers, our devices use
          <span v-b-tooltip.hover.v-info title="A way to store information on a device" class="highlighted-word"> local storage. </span>
          They save the data so we can use it later! Some examples of this are:
        </p>
        <b-row class="row-cols-1 row-cols-md-3 mb-5">
          <StorageExample iconName="controller" title="Gaming Consoles" description="You save your video game, and that information gets stored in the console!"/>
          <StorageExample iconName="chat-dots-fill" title="Messaging App" description="Most messaging apps automatically store old messages so you can read them later."/>
          <StorageExample iconName="folder-fill" title="Filing Cabinet" description="You store and organize paperwork here."/>
        </b-row>
        <br>
        <p class="mb-5">
          Local storage is sometimes called a <span v-b-tooltip.hover.v-info title="An organized collection of information stored on a device" class="highlighted-word">local database</span>.
          A <span v-b-tooltip.hover.v-info title="an organized collection of information" class="highlighted-word">database</span>
          is an organized collection of information, like this:
        </p>
        <div class="database-outline mb-4">
          <p> My Database </p>
          <b-row class="mb-2">
              <DataTable v-for="table in tables" v-bind:key="table.id" v-bind:class="table.classes" v-bind:items="table.items"/>
          </b-row>
        </div>
        <p>
          When we access a database, we <span class="highlighted-word"> call </span>
          it, or <span class="highlighted-word"> make a call </span> to it. We can do many things in a database, like:
        </p>
        <b-row class="d-flex justify-content-around mb-3">
          <b-button class="mb-2" variant="info" v-on:click="get">Get Information</b-button>
          <b-button class="mb-2" variant="success" v-on:click="add">Add Information</b-button>
          <b-button class="mb-2" variant="warning" v-on:click="update">Update Information</b-button>
          <b-button class="mb-2" variant="danger" v-on:click="remove">Delete Information</b-button>
        </b-row>
        <p align="center" class="text-muted prompt-text"> Try pressing the buttons! </p>
        <br>

        <h3 class="mb-3 text-muted"> Key-Pair Values </h3>
        <p> In a database, information is stored in <span class="highlighted-word"> key-pair values</span>.
            They're similar to variables! The <span class="highlighted-word">key</span>
            is like the name of the <span class="highlighted-word">value</span>, or information, in the database.
        </p>
        <b-row class="justify-content-center my-2">
          <b-col col md="2" class="my-auto"> <p class="mb-0 font-weight-bold"> Key </p></b-col>
          <b-col col md="2"><b-icon-arrow-right font-scale="3"/></b-col>
          <b-col col md="6" class="my-auto"><p class="mb-0 font-weight-bold"> Value </p></b-col>
        </b-row>
        <KeyValue v-for="table in tables" v-bind:key="table.id" v-bind:name="table.id" v-bind:items="table.items"/>
        <p> We use the key to tell the database which piece of information to get, add, update, or delete. Let's see how to do it in App Inventor and Thunkable! </p>

        <h2> Using the Tiny DB and Local Storage Components </h2>
        <p> We use the <span class="highlighted-word">TinyDB component</span> in App Inventor, and the <span class="highlighted-word">Local Storage component</span> in Thunkable.
            It is important to know that TinyDB and Local Storage only allows you to store data <span class="highlighted-word">locally</span>. This means that two users cannot share data with the same TinyDB or Local Storage.  When a user stores data into TinyDB or Local Storage,
            it will only be available on her phone, and no one else’s. To use TinyDB or Local Storage, drag it onto your screen through the designer. You can find it under the storage menu in App Inventor and the data menu in Thunkable.
            It will appear as a non-visible component and will look like this:
        </p>
        <b-row class="justify-content-center text-center">
          <b-col col md="3"><h4> App Inventor </h4></b-col>
          <b-col col md="3"><h4> Thunkable </h4></b-col>
        </b-row>
        <PictureRow v-bind:pictures="images.slice(0,2)"/>
        <p> You can talk to your TinyDB or Local Storage by <span class="highlighted-word">making calls</span> to it. When you make a call, you can store things and get things from it.
            The way you store data is by giving it a “tag” in App Inventor or a “key” in Thunkable. This is a name that you will use to retrieve the data.
            It is a lot like a variable name. If you use the same tag name or key name to store data twice, the TinyDB or Local Storage will overwrite, or erase,
            the old data with the new data. This can be useful if you need to update what’s in your storage, but you should be careful never to repeat names otherwise!
            Here are a few examples of how to make calls to TinyDB and Local Storage:
        </p>
        <b-row class="justify-content-center text-center">
          <b-col col md="2"></b-col>
          <b-col col md="3"><h4> App Inventor </h4></b-col>
          <b-col col md="3"><h4> Thunkable </h4></b-col>
        </b-row>
        <PictureRow v-bind:pictures="images.slice(2,4)" label="Store or Save"/>
        <PictureRow v-bind:pictures="images.slice(4,6)" label="Get"/>
        <p> Above, we stored our fruits list with the tag/key “Food”. The second block shows how to retrieve the fruits list from storage.
            The tag/key needs to be typed exactly as it was when the data was stored, including all capital letters. To better understand this,
            let’s walk through an example. Let’s say you needed to store three things in a database. One is the Fruits lists, one of them is your age,
            and the other is a list of your favorite things to do. You make three calls to the database like this:
        </p>
        <b-row class="justify-content-center text-center">
          <b-col col md="3"><h4> App Inventor </h4></b-col>
          <b-col col md="3"><h4> Thunkable </h4></b-col>
        </b-row>
        <PictureRow v-bind:pictures="images.slice(2,4)"/>
        <PictureRow v-bind:pictures="images.slice(6,8)"/>
        <PictureRow v-bind:pictures="images.slice(8,10)"/>
        <p> You now have three entries in your database, and can you guess what they look like? </p>
        <b-row class="row-cols-1 row-cols-md-3 mb-2 text-center">
          <b-col><b>Tag/Key Name: Food</b></b-col>
          <b-col><b>Tag/Key Name: MyAge</b></b-col>
          <b-col><b>Tag/Key Name: Favorites</b></b-col>
        </b-row>
        <b-row class="row-cols-1 row-cols-md-3 mb-5">
          <StorageExample iconName="cart-fill" title="Value" description="['Apples', 'Bananas', 'Oranges']"/>
          <StorageExample iconName="person-fill" title="Value" description="16"/>
          <StorageExample iconName="star-fill" title="Value" description="['Learn How To Code', 'Visit Family', 'Listen to Music']"/>
        </b-row>
        <p class="note-text"><b>Note:</b> For a refresher on how lists work, reference <a class="highlighted-word" href="https://technovationchallenge.org/curriculum/coding-6/">Coding 6: Lists</a></p>


        <p> Now, when you want to retrieve your favorite things, you make a call like this: </p>
        <b-row class="justify-content-center text-center">
          <b-col col md="3"><h4> App Inventor </h4></b-col>
          <b-col col md="3"><h4> Thunkable </h4></b-col>
        </b-row>
        <PictureRow v-bind:pictures="images.slice(10,12)"/>
        <p> When you use this block you will get “Learn how to Code Visit Family Listen to Music”. Now let’s say you want to retrieve your age, so you make a call like this: </p>
        <PictureRow v-bind:pictures="images.slice(12,14)"/>
        <p> When you use this block you just get a blank string: “ ”. This is because the tag “myage” does not exist in your database! However, the tag “MyAge” does exist.
            Since your database did not recognize the tag, it defaulted to show you the block next to “valueIfTagNotThere”, which is a blank string. You can make this string say anything you want.
            You can even make it be an error message to your user.
        </p>
        <p class="note-text"><b>Note:</b> In App Inventor, if you create an app with multiple screens, components and variables will not be able to talk to each other between each screen. You can use TinyDB to transfer information from one screen of your app to another. Visit this page for more information: <a class="highlighted-word" href="http://appinventor.mit.edu/explore/ai2/concepts.html#Screens"> MIT Screens.</a> </p>
      </div>
    </section>
    <section id="Activity" class="activity-bg py-5">
      <div class="container">
        <h2 class="font-weight-bold" id="activity">Activity: Fixing a To-Do List</h2>
        <p> This To-Do List lets the user create a to-do list that will be remembered each time they open and close their app. However, the source code has a bug. The app never remembers any tasks the user adds or deletes. Can you figure out how to fix it? </p>
        <b-row align-h="center" class="mb-3">
          <b-button variant = "warning" class="mr-5 font-weight-bold" href="https://accounts.google.com/o/oauth2/auth?state=YiYAAWAU1rQAUiLGjSqdYqHRbIUcyZmK&redirect_uri=http://login.appinventor.mit.edu/complete/google-oauth2/&response_type=code&client_id=835377224499-p6kuf1tm823g8vmvkpl7urs5r0gfasns.apps.googleusercontent.com&approval_prompt=force&scope=profile+email">App Inventor Code</b-button>
          <b-button variant = "warning" class="ml-5 font-weight-bold" href="https://x.thunkable.com/copy/dcf7f893a0be54269f489447d741f672">Thunkable Code</b-button>
        </b-row>
        <p>If you’re stuck, check out this App Inventor video solution by Technovation alumni Jennifer John:</p>
        <div>
          <b-embed
            type="iframe"
            aspect="16by9"
            src="https://www.youtube.com/embed/FCL_D9mBzpE"
            allowfullscreen
          ></b-embed>
        </div>
      </div>
    </section>
    <section id="Reflection" class="reflect-bg py-5">
      <div class="container">
        <h2 class="font-weight-bold" id="reflect">Reflection</h2>
        <p> Now that you’ve learned how to store data on your phone, you should brainstorm with your team where you might use this in your app. The next coding lesson will teach you how to store information in the cloud that is not only accessible on the user’s phone but anywhere that they login to their account. </p>
      </div>
    </section>
  </div>
</template>

<script>
import KeyTerm from './components/KeyTerm.vue'
import SectionNav from './components/SectionNav.vue'
import StorageExample from './components/StorageExample.vue'
import DataTable from './components/DataTable.vue'
import KeyValue from './components/KeyValue.vue'
import PictureRow from './components/PictureRow.vue'
import imageUrls from './image-urls.js'
export default {
  name: 'App',
  components: {
    KeyTerm,
    SectionNav,
    StorageExample,
    DataTable,
    KeyValue,
    PictureRow
  },
  data: function() {
    return {
      tables: [ { id: 'Foods', classes: 'table-success mx-4' , items: [{food: 'Apples'}, {food: 'Bananas'}, {food: 'Oranges'}] },
                { id: 'Favorites', classes: 'table-secondary mx-4', items: [{favorites: 'Learn to Code'}, {favorites: 'Visit Family'}, {favorites: 'Listen to Music'}] },
                { id: 'Pets', classes: 'table-warning mx-4', items: [{pets: 'Dogs'}, {pets: 'Cats'}, {pets: 'Birds'}] }
              ],
      keyTerms: [ { iconName: "key", title: "Key-Pair Value", color: "#ff9c91", description: "A way to store information" },
                  { iconName: "basket2", title: "Local Storage", color: "#ffe291", description: "A way to store information on a device"  },
                  { iconName: "cloud", title: "Database", color: "#d3ff91", description: "An organized collection of information" },
                  { iconName: "laptop", title: "Local Database", color: "#91ffcc", description: "An organized collection of information stored on a device" },
                  { iconName: "telephone-inbound-fill", title: "Calling a Database", color: "#91c4ff", description: "This allows you to store, get, update or delete information in the database" },
                  { iconName: "cloud-fill", title: "TinyDB", color: "#b991ff", description:"A database service you can use in App Inventor that allows you to store information on a device"  },
                  { iconName: "basket3", title: "Local Storage (Thunkable Component)", color: "#ff91b9", description: "A component in Thunkable that lets you store information on your device" }
                ],
      images: imageUrls,
      sideNavVisible: false
    }
  },
  methods: {
    get: function(){
      this.tables[1].classes = 'table-info mx-4';
    },
    add: function(){
      let table= {id: 'Drinks', classes: 'table-primary mx-4', items: [{drinks: 'Coffee'}, {drinks: 'Tea'}, {drinks: 'Soda'}]}
      if(!this.tables.some(t => t.id === table.id))
        this.tables.push(table);
    },
    update: function(){
      this.tables[0].items = [{food: 'Fried Rice'}, {food: 'Kiwi'}, {food: 'Hamburger'}]
    },
    remove: function(){
      this.tables.shift();
    },
    activateSideNav: function(isVisible){
      if(!isVisible){
        this.sideNavVisible = true;
      }else{
        this.sideNavVisible = false;
      }
    }
  }
}
</script>

<style>
html{
  scroll-behavior: smooth;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 20px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
.highlighted-word{
  color: green;
  font-weight: bold;
}
.database-outline{
  border: 4px solid gray;
  border-radius: 0.5%;
  padding: 10px;
  text-align: center;
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.prompt-text{
  font-size: 20px;
  animation: pulsate 2s ease-out;
  animation-iteration-count: infinite;
  opacity: 0.5;
}
.activity-bg{
  color: white;
  background-color: #43b12b;
}
.reflect-bg{
  color: white;
  background: linear-gradient(45deg, #0474d4 50%, #5dbcd2 50%);
}
.side-nav{
  position: fixed;
  top: 40%;
  right: 20px;;
  z-index: 1;
  border-radius: 500px;
  background: rgb(222, 222, 222);
  background: rgba(222, 222, 222, 0.6);
  transition: opacity 1s;
}
.side-nav-icon{
  color: #43b12b;
}
.note-text{
  font-style: italic;
  font-size: 15px;
}
@keyframes pulsate {
    0% {
        opacity: 0.2;
    }
    50% {
        opacity: 1.0;
    }
    100% {
        opacity: 0.2;
    }
}
</style>
