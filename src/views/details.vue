<template>
    <div class="sidegrid">
      <nav class="sidebar">
        <img src="@/assets/elephant.png" alt="" id="ticker">
        <router-link to="/" id="home">Home</router-link> 
        <router-link :to="{name:'details'}" id="details">Elephant</router-link>
      </nav>
    </div>
    <div id="acumen">
      <p id="text">Acumen Digital Interview Task / Elephantom > Elephant</p>
    </div>
    <div class="imgwrapper">
      <img :src="elephant.image" alt="Elephant image"  id="image">
      <h3 class="tuffi">{{elephant.name}}<span id="female">{{elephant.sex}}</span></h3>
      <hr class="single">
      <h2 class="circus">{{elephant.note}}</h2>
    </div>
</template>

<script>
export default {
  created(){
   this.getElephantDetails()
  },

  methods: {
    getElephantDetails () {
      fetch(`https://acumen-elephantom.herokuapp.com/elephants/id/${this.$route.query.id}`)
      .then((response) => response.json())
      .then((data)=>{
      console.log(data)
      this.elephant = data.data;
      })
    }
  },
  data(){
    return{
      elephant:[],
    }
  }
}
</script>

<style scoped>

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

.imgwrapper{
margin-left: 361px;
margin-top: 93px;
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


#image{
width: 934px;
height: 431px;
margin: 27px auto 0 55px;
}


.tuffi{
font-family: 'Overpass';
font-style: normal;
font-weight: 700;
font-size: 48px;
line-height: 61px;
color: #30425A;
margin: 43px 0 0 61px;
}

#female{
margin-left: 13px;
font-family: 'Overpass';
font-style: normal;
font-weight: 400;
font-size: 18px;
line-height: 23px;
color: #30425A;
}

hr.single{
width: 920.5px;
height: 0px;
padding: 0;
margin: 16px auto 0 61px;
}

.circus{
width: 934px;
font-family: 'Overpass';
font-style: normal;
font-weight: 400;
font-size: 24px;
line-height: 30px;
color: #30425A;
margin: 20px auto 40px 61px;           
}
</style>
