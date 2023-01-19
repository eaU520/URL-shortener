<script>
import axios from "axios";
export default{
    data(){
        return {
            URLtext: '',
            URLshort: ''
        }
    },
    methods: {
        //Body {"long_url": "http://www.http.test.com.too_long/way_toolong"}
        //Authorization: Bearer 346c0ceeb0de2801ee05bf54dcdbed92045095ed
        //Content-Type: application/json
        //Content-Length: ????
        //Accept: application/json
        /*
        var fetch = require('node-fetch');

fetch('https://api-ssl.bitly.com/v4/shorten', {
    method: 'POST',
    headers: {
        'Authorization': 'Bearer {TOKEN}',
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({ "long_url": "https://dev.bitly.com", "domain": "bit.ly", "group_guid": "Bmc53Vqc1YH" })
});


        */
        shortenAPICall(event){
            const token = "346c0ceeb0de2801ee05bf54dcdbed92045095ed";
            // alert("Test, to call API: with "+this.URLtext)
            //Axios.defaults.headers.post['Authorization'] = `Bearer ${localStorage.getItem('access_token')}`;
            const stuffs = {
                'Authorization': 'Bearer '+token,
                'Content-Type': 'application/json'
            };
            try{
             const response = await axios.post("https://api-ssl.bitly.com/v4/shorten",{
              headers: stuffs,
              body: JSON.stringify({"long_url": this.URLtext, "domain": "bit.ly", "group_guid":"Bmc53Vqc1YH"})
            })}
            catch (e){
              console.log(e);
            }
            this.URLshort = JSON.stringify(response.link);
            },
        }
      }
</script>

<template>
  <div class="URL_input">
    <h3>
      Input a URL
        <p>The original URL is: {{ URLtext }}</p>
        <p>The shortened URL is: {{ URLshort }}</p>
        <input v-model="URLtext" placeholder="Put in a URL" />
        <button @click="shortenAPICall">Shorten!</button>
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}


/* @media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
} */
</style>
