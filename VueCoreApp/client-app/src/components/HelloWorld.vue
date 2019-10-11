<template>
    <div>
        <blockquote>
            &#8220;{{ quote }}&#8221;
            <footer>
                <small>
                    <em>&mdash;{{ author }}</em>
                </small>
            </footer>
        </blockquote>
        <div v-if="forecasts">
            <div v-for="forecast in forecasts">
                <span> Summary             {{forecast.summary}}</span><br />
                <span> Date Formatted             {{forecast.dateFormatted}}</span><br />
                <span>{{forecast.temperatureC}} Celcius</span>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'HelloWorld',
        props: {
          quote: String,
          author: String,
        },
        data: function(){
            return{
                forecasts: null
            }
        },
        mounted: function () {
            this.getForecast();
        },
        methods: {
            getForecast: function () {
                var self = this;
                axios.get('api/SampleData/WeatherForecasts')
                .then((response) => {
                    self.forecasts = response.data;
                })
                .catch((e) => {
                    this.showError = true;
                    this.errorMessage = `Error while loading weather forecast: ${e.message}.`;
                })
                .finally(() => (this.loading = false));
            }
        }
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
