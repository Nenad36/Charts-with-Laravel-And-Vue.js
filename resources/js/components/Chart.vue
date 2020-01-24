<script>
    import { Bar } from 'vue-chartjs'
    export default {
        name: "Bar",
        extends: Bar,
        data() {
            return {
                url: 'http://charts.test/products',
                years: [],
                labels: [],
                prices: [],
                data: ''
            }
        },
        methods: {
            getProducts(){
                axios.get(this.url).then((response)=>{
                    this.data = response.data;
                    if(this.data){
                        this.data.forEach(element => {
                            this.years.push(element.year);
                            this.labels.push(element.name);
                            this.prices.push(element.price);
                        });
                        this.renderChart({
                            labels: this.years,
                            datasets: [
                                {
                                    label: 'Sales',
                                    backgroundColor: '#b3d9ff',
                                    data: this.prices
                                }
                            ]
                        }, {responsive: true, maintainAspectRatio: false});
                    }
                    else {
                        console.log('NO DATA');
                     }
                });
            }
        },
        mounted() {
            this.getProducts();
        }
    }
</script>

