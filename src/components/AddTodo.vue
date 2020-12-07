<template>
    <div id="app" :class="typeof weather.main !='undefined'&& this.pic.endsWith('n') ? 'noc':''">
        <header>
                <nav>
                    <div class="logo">
                        <h4>World Weather</h4>
                    </div>
                    <ul class="nav-linkovi">
                        <li><a href ="#">Home</a></li>
                        <li><a href ="#">About</a></li>
                        <li><a href ="#">Help</a></li>
                        <li><a href ="#">Contact </a></li>
                    </ul>
                </nav>
            </header>
        <main>
            <div class="okvir">
                <input type="text" class="traka" placeholder="Upisite ime grada..." v-model="query" @keypress="fetchWeather"/>
            </div>
            <div class="Podaci" v-if="typeof weather.main !='undefined'">
                <div class="LokacijaVrijeme">
                    <div class="Lokacija">{{weather.name}},  {{weather.sys.country}}</div>
                    <div class="Vrijeme">{{dateBuilder()}}</div>
                </div>
                <div class="TempStanje">
                    <div class="Temperatura">{{Math.round(weather.main.temp)}}°C<br/>
                        <img :src="'https://openweathermap.org/img/wn/'+this.pic+'@4x.png'"/><br/>
                        <div class="Stanje">{{weather.weather[0].description}}</div>
                    </div>
                    <div class="Vjetarivlaznost">Vjetar: {{Math.round(weather.wind.speed)}}  km/h <span class="tab"></span> Vlažnost zraka: {{Math.round(weather.main.humidity)}}%</div>
                </div>
            </div>
        </main>
        <footer>
            © Copyright PWA 2020
        </footer>
    </div>
</template>

<script>
export default {
    data(){
        return{
            api_key:'309ce81e0c0cfabb8d51b5fac2506df5',
            url_base:'http://api.openweathermap.org/data/2.5/',
            query:'',
            weather:{},
            pic: {},
        }
    },
    methods:{
        fetchWeather (e){
            if(e.key=="Enter"){
                fetch(`${this.url_base}weather?q=${this.query}&units=metric&lang=hr&APPID=${this.api_key}`)
                    .then(res=> {
                        return res.json();
                    }).then(this.setResults);
            }
        },
        setResults(results){
            this.weather=results;
            this.pic =results.weather[0].icon
        },
        dateBuilder (){
            let d = new Date()
            let months=["Siječanj","Veljača","Ožujak","Travanj",
            "Svibanj","Lipanj","Srpanj","Kolovoz",
            "Rujan","Listopad","Studeni","Prosinac"];

            let days=["Ponedjeljak","Utorak","Srijeda",
            "Četvrtak","Petak","Subota","Nedjelja"];

            let day= days[d.getDay()];
            let date= d.getDate();
            let month= months[d.getMonth()];
            let year= d.getFullYear();

            return `${day}, ${date}. ${month} ${year}`;
        }
    }
}
</script>
<style>

* { 
    margin:0;
    padding:0;
    box-sizing:border-box;
}
nav{
    display:flex;
    justify-content: space-around;
    align-items: center;
    min-height: 12vh;
    background-color: black;
    font-family: 'Poppins', sans-serif;
}
.logo{
    color:white;
    text-transform: uppercase;
    letter-spacing: 5px;
    font-size: 35px;
}
.nav-linkovi{
    display:flex;
    justify-content: space-around;
    width:30%;
}
.nav-linkovi li{
    list-style:none;
}
.nav-linkovi a{
    color:white;
    font-weight: bold;
    font-size:15px;
    letter-spacing:4px;
    text-decoration:none;
}
body {
    font-family:"montserrat", sans-serif;
}
#app {
    background-size:cover;
    background-position: top;
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.3)),url('../assets/pozadina.jpg');
}
#app .noc{
    background-size:cover;
    background-position: top;
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.5), rgba(0,0,0,0.9)),url('../assets/pozadina.jpg');
}

main {
    font-family:"montserrat", sans-serif;
    min-height: 100vh;
    padding:25px;
}
.okvir{
    width:100;
    margin-bottom: 30px;

}
.okvir .traka{
    display:block;
    width:100%;
    padding:15px;
    color:black;
    font-size:20px;

    appearance: none;
    border:none;
    outline:none;
    background:none;

    box-shadow:0px 0px 20px rgba(0,0,0,1);
    background-color:rgb(255,255,255,0.5);
    border-radius: 0px 16px 0px 16px;
}
.okvir .traka:hover{
    background-color: rgba(255,255,255,0.75);
    box-shadow: 0px 0px 20px rgba(0,0,0,0.25);
    border-radius: 20px 20px 20px 20px
}
.LokacijaVrijeme .Lokacija{
    color:white;
    font-size:35px;
    font-weight: 700;
    text-align: center;
    text-shadow: 1px 3px rgba(0,0,0,0.25);
}
.LokacijaVrijeme .Vrijeme{
    color:white;
    font-size:18px;
    font-weight: 300;
    text-align: center;
    font-style: italic;
    text-shadow: 1px 3px rgba(0,0,0,0.25);
}
.TempStanje{
    text-align: center;
}
.TempStanje .Temperatura{
    display:inline-block;
    padding: 30px 50px;
    color:white;
    font-size:100px;
    font-weight: 900;
    text-shadow: 3px 6px rgba(0,0,0,0.25);
    background-color: rgba(255,255,255,0.3);
    border-radius: 20px;
    margin: 30px 0px;
    box-shadow: 5px 8px rgba(0,0,0,0.5);
}

.TempStanje .Stanje{
    color:white;
    font-size:40px;
    font-weight:700;
    font-style:italic;
    text-shadow: 4px 5px rgba(0,0,0,0.25);
    margin:-70px 0px 0px 0px;
}

.TempStanje .Vjetarivlaznost{
    color:white;
    font-size:27px;
    font-weight:600;
    text-shadow: 2px 4px rgba(0,0,0,0.25);
    margin-top:20px;
}
 .tab { 
            display: inline-block; 
            margin-left: 25px; 
        }

footer{
    background-color: black;
    display:flex;
    justify-content: space-around;
    align-items: center;
    min-height: 8vh;
    color:white;
}

</style>
