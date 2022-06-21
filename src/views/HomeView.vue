<template>
  <div class="sidegrid">
  <nav class="sidebar">
  <img src="@/assets/elephant.png" alt="" id="ticker">
  <router-link to="/" id="home">Home</router-link> 
  <router-link :to="{name:'details'}" id="details">Elephant</router-link>
  </nav>
  </div>
   <div id="acumen">
  <p id="text">Acumen Digital Interview Task / Elephantom</p>
  </div>
  <div class="tableholder">
  <table class="table">
    <caption class="top" id="all">All Elephants</caption>
  <thead>
  <tr class="top" id="sn">
    <td class="sign">S/N</td>
    <td>Name</td>
    <td>Species</td>
    <td>sex</td>
    <td>Affiliation</td>
    <td class="sixth">Dob</td>
  </tr>
   </thead>
  <tbody>
  <tr v-for="(elephant, index) in asianelephants" :key="elephant._id" class="row" @click="$router.push(`/details?id=${elephant._id}`)">
    <td class="sign">{{ index + 1}}</td>
    <td>{{elephant.name}}</td>
    <td>{{elephant.species}}</td>
    <td>{{elephant.sex}}</td>
    <td>{{elephant.affiliation}}</td>
    <td class="sixth">{{elephant.dob}}</td>
  </tr>
  </tbody>
</table>
  <div class="page">
  <p>PAGE 1 0F 10</p>
  <div class="buttons">
  <router-link :to="{ name: 'details'}" style="text-decoration: inherit; color: white;" id="btn1"> &lt; </router-link>
  <router-link :to="{ name: 'details'}" style="text-decoration: inherit; color: #0546E0;" id="btn2"> 1 </router-link>
  <router-link :to="{ name: 'details'}" style="text-decoration: inherit; color: inherit;" id="btn3"> 2 </router-link>
  <router-link :to="{ name: 'details'}" style="text-decoration: inherit; color: #C4CDD5;" id="btn4"> > </router-link>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  // components: {
  //  details: details, 
  // },
  created(){
    this.getAsianElephants()
  },
  methods: {
    getAsianElephants(){
      fetch('https://acumen-elephantom.herokuapp.com/elephants/asian')
    .then((response) => response.json())
    .then((data)=>{
      this.asianelephants = data.data;
      })
    }
  },
  data(){
    return{
      asianelephants:[]
    }
  }
}
</script>

<style scoped>
.wrapper {
display: grid;
height: 100vh;
width: auto;
grid-template-columns: repeat(10,1fr);
grid-template-rows: 1fr;
column-gap: 0;
row-gap: 0;
top: 0;
bottom: 0;
left: 0;
right: 0;
}

#ticker{
align-self: center;
width: 191px;
height: 191px;
left: 85px;
margin-top: 5.5%;
border-radius: 50%;
max-width: auto;
height: auto;
display: block;
margin-left: auto;
margin-right: auto;
}

.sidegrid{
width: 361px;
position: fixed;
height: 100vh;
top: 0;
left: 0;
bottom: 0;
}

.sidebar{
top: 0;
left: 0;
bottom: 0;
height: 100vh;
width: 361px;
background: #DDDDFF;
display: flex;
flex-direction: column;
align-items: center;
position: fixed;
}

nav a{
text-decoration: inherit;
min-width: 100%;
text-align: center;
}

nav a.router-link-exact-active {
background: #B9B9FF;

}

#home{
height: 62px;
margin-top: 5.8%;
line-height: 62px;
font-family: 'Overpass';
font-style: normal;
font-weight: 400;
font-size: 18px;
color: #FFFFFF;
}

#details{
width: auto;
height: 62px;
left: 0px;
top: 385px;
font-family: 'Overpass';
font-style: normal;
font-weight: 400;
font-size: 18px;
line-height: 62px;
color: #30425A;
}

#acumen{
top: 0;
position: fixed;
width: 1079px;
height: 93px;
margin-left: 361px;
background: #FFFFFF;
box-shadow: 0px -7px 24px rgba(0, 0, 0, 0.25);
white-space: wrap;
overflow: normal;
}

#text{
color: #30425A;
font-family: 'Overpass';
font-style: normal;
font-weight: 400;
font-size: 18px;
line-height: 93px;
color: #30425A;
margin: auto auto auto 35px
}

.tableholder{
margin: 153px auto 0 396px;
width: 939px;
height: auto;
box-shadow: 0px 3px 10px -3px rgba(0, 0, 0, 0.25);
background: #FFFFFF;
}

table, th, td {
border: none;
border-collapse: collapse;
}


.table{
width: 939px;
margin-top: 0;
margin-bottom: 6.1vh;
margin-left: 0;
margin-right: 0;
height: auto;
border: none;
}

.row{
height: 75px;
text-align: center;
color: #848383;
cursor: pointer;        
}

.top{
height: 75px;
text-align: center;
color: #000000;
}

#all{
text-align: left;
margin-left: 1.8vw;
color: #30425A;
line-height: 75px;
}

#sn{
background: #E5E5E5;
}

.row:nth-child(even){
background: #F5F5F5;
}

.page{
font-family: 'Graphik';
font-style: normal;
font-weight: 400;
font-size: 14px;
line-height: 15px;
color: #30425A;
opacity: 0.9;
margin: 0 auto 0 auto;
white-space: nowrap;
overflow: hidden;
display: flex;
align-items: center;
width: 210px;
}

.buttons{
white-space: nowrap;
overflow: hidden;
}

#btn1{
box-sizing: border-box;
width: 20px;
height: 20px;
line-height: 20px;
background: #919EAB;
opacity: 0.5;
border-radius: 4px;
margin-right: 8px;
margin-left: 20px;
display: inline-block;
text-align: center;
color: white;

}

#btn2{
box-sizing: border-box;
background: #FFFFFF;
border: 1px solid #0546E0;
border-radius: 4px;
width: 20px;
height: 20px;
line-height: 20px;
margin-right: 8px;
display: inline-block;
text-align: center;
font-family: 'SF Pro Text';
font-size: 14px;
line-height: 20px;
text-align: center;
color: #0546E0;

}

#btn3{
box-sizing: border-box;
background: #FFFFFF;
border: 1px solid #DFE3E8;
border-radius: 4px;
margin-right: 8px;
width: 20px;
height: 20px;
line-height: 20px;
display: inline-block;
text-align: center;
font-family: 'SF Pro Text';
font-style: normal;
font-weight: 700;
font-size: 14px;
color: #212B36;

}

#btn4{
box-sizing: border-box;
width: 20px;
height: 20px;
line-height: 20px;
background: #FFFFFF;
border: 1px solid #DFE3E8;
border-radius: 4px;
display: inline-block;
text-align: center;
margin: auto;
color: #C4CDD5;
}
</style>
