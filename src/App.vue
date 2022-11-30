<script setup lang="ts">
const categories = [
    {
        name: 'category1',
        subcategories: [
            {
                name: 'category2',
                subcategories: []
            },
            {
                name: 'category3',
                subcategories: [
                    {
                        name: 'category4',
                        subcategories: []
                    }
                ]
            }
        ]
    },
    {
        name: 'category5',
        subcategories: []
    }
];


// TO-DO: Implement this function
const getCategoryPath = (categories, categoryName) => {
    let path:any;
    

     categories.map((item, index) => {
      if (item.name!=categoryName&& item.subcategories!=''){
        path='/'+item.name
        let subcategories=item.subcategories
        subcategories.map((i, key)=>{
          if (i.name!=categoryName&& i.subcategories!=''){
            if(categoryName==i.subcategories[0].name){
              path+='/'+i.name+'/'+i.subcategories[0].name
              
            }

          }
          if (i.name==categoryName){
            path+='/'+i.name
          }
        })
        
      }
      if(item.name==categoryName){
        path='/'+item.name
      }
       
      });
      return path
};

// OUTPUT SAMPLES
// getCategoryPath(categories, 'category4')
console.log(getCategoryPath(categories, 'category4')); // should output: '/category1/category3/category4'
console.log(getCategoryPath(categories, 'category2')); // should output: '/category1/category2'
console.log(getCategoryPath(categories, 'category5')); // should output: '/category5'

</script>
<template>
  <h1>hola</h1>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
