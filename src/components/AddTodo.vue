<template>
    <div id="app">
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
                <input type="text" class="traka" placeholder="Search City..."/>
            </div>
            <div class="Podaci">
                <div class="LokacijaVrijeme">
                    <div class="Lokacija">Zagreb,CRO</div>
                    <div class="Vrijeme">Subota, 31.10.2020</div>
                </div>
                <div class="TempStanje">
                    <div class="Temperatura">15°C</div>
                    <div><img src="../assets/svg/wi-day-sunny.svg" alt="Sunce" width="200" height="200"></div>
                    <div class="Stanje">Sunčano</div>
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
    background-image: url('../assets/pozadina.jpg');
    background-size:cover;
    background-position: top;
}
main {
    font-family:"montserrat", sans-serif;
    min-height: 100vh;
    padding:25px;
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.5));
}
.okvir{
    width:100;
    margin-bottom: 30px;
}
.okvir .traka{
    display:block;
    width:100%;
    padding:15px;
    color:peru;
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
img{
    filter: invert(100%);
    margin:-20px;
}
.TempStanje .Stanje{
    color:white;
    font-size:40px;
    font-weight:700;
    font-style:italic;
    text-shadow: 4px 5px rgba(0,0,0,0.25);
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
