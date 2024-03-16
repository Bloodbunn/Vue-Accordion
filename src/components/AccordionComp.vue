<template>

<div  class="w-2/3 max-[900px]:w-[90%] mx-auto">
  <div v-for="(item, index) in items" :key="index" class="mb-2">
    <h1 @click="toggleAccordion(index)" class=" hover:bg-cyan-700 transition-all duration-200 ease-linear w-full p-3 bg-blue-500 text-xl text-white font-bold">{{ item.title }} 
    <span> {{ item.open ? "🔽" : "▶️" }}</span> </h1>   
   <p v-show="item.open" class="mb-2 p-2 border border-gray-400 bg-gray-100 text-gray-600 transition-all duration-300">{{ item.content }} </p> 
  </div>
   
</div>

</template>



<script setup>
import {ref} from 'vue'
const items = ref([
{
    title: "What is HTML?",
    content:
      "The HyperText Markup Language or HTML is the standard markup language for documents designed to be displayed in a web browser. It defines the content and structure of web content. It is often assisted by technologies such as Cascading Style Sheets and scripting languages such as JavaScript.",
    open: false,
  },
  {
    title: "What is CSS?",
    content:
      "Cascading Style Sheets is a style sheet language used for specifying the presentation and styling of a document written in a markup language such as HTML or XML. CSS is a cornerstone technology of the World Wide Web, alongside HTML and JavaScript.",
    open: false,
  },
  {
    title: "What is JS?",
    content:
      "JavaScript, often abbreviated as JS, is a programming language and core technology of the World Wide Web, alongside HTML and CSS. As of 2023, 98.7% of websites use JavaScript on the client side for webpage behavior, often incorporating third-party libraries.",
    open: false,
  },
])

const toggleAccordion = (index) => { 
    items.value = items.value.map((item, i) => ({
        ...item,

        open:  i === index ? !item.open : item.open, 

    }))
}
/* if the indexes match, then it makes it from false to treu thereby opening it (!item.open), if it does not match, meaning
those that are not clicked, then they keep their current value of item.open, so if they are open they stay open, if they
are closed they stay closed. if we want to close them you have to do like this:
!item.open : false,
this closing every other one that is not clicked.
*/






</script>

<!-- 
    This code defines an array of items, each representing a section in an accordion component. 
    Each item has a `title`, `content`, and `open` property. The `open` property is used to track whether 
    the section is currently open or closed.

The `toggleAccordion` function is responsible for toggling the state of an accordion section. It takes an `index` parameter,
 which indicates the index of the item to toggle.

Here's how the `toggleAccordion` function works:

1. It uses the `map` method to iterate over each item in the `items` array.
2. For each item, it spreads its properties using the spread syntax (`...item`) to create a new object.
3. It updates the `open` property based on whether the index of the current item matches the index passed to the 
function (`i === index`). (the map method like the v-for iterates through the child objects the items array, takes out
their propeties and gives the index (here being called i) of each of them. so if index = i, it then does the logic. )
   - If the indices match, it toggles the value of the `open` property (`!item.open`), i.e., if it was `true`, it becomes
    `false`, and vice versa.
   - If the indices don't match, it sets the `open` property to `false`, effectively closing the other accordion sections.
4. It returns the updated array of items.

By toggling the `open` property of the selected item while ensuring that all other items have their `open` property 
set to `false`, this function enables the accordion to expand or collapse sections as desired, providing a user-friendly 
interface for navigating the content.
-->