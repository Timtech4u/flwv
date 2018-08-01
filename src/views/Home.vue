<template>
  <b-container class="bv-example-row">
    <b-row>
        <b-col>
            <b-button size="lg" variant="outline-success" @click="showPay()">
                Collect Payment In
                <span> 
                    This would help you generate a payment URL. <br>
                    Enter email: <input type="text" v-model="email"><br>
                    Enter amount: <input type="number" v-model="amount"> <br>
                    <b-button size="sm" variant="success" @click="acceptPay()"> 
                        Oya Pay Now
                    </b-button>
                    <br>
                    <strong> Payment Link: {{paymentLink}} </strong>
                </span>
            </b-button>
        </b-col>
        <b-col>
            <b-button size="lg" variant="outline-success">
                Make Transfers Out
            </b-button>
        </b-col>
    </b-row>
    <b-row>
        <b-col>
          <b-button size="lg" variant="outline-success">
                Collect Merchants Payments
            </b-button>
        </b-col>
        <b-col>
          <b-button size="lg" variant="outline-success">
                Receive Airtime or Rewards
            </b-button>
        </b-col>
    </b-row>    
    <b-row>
        <b-col>
          <b-button size="lg" variant="outline-success">
                Pay Recurring Service
            </b-button>
        </b-col>
        <b-col>
          <b-button size="lg" variant="outline-success">
                Perform KYC Service..
            </b-button>
        </b-col>
    </b-row>
</b-container>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      apiUrl: 'https://api.ravepay.co/flwv3-pug/getpaidx/api/v2/hosted/pay',
      email: '',
      amount: '',
      showpay: true,
      paymentLink: ''
    }
  },
  methods: {
    showPay(){
        return !this.showpay
    },
    acceptPay() {
        axios.post(this.apiUrl, {
            PBFPubkey: "FLWPUBK-dd88c1196b35983b3c37b8d9e22b7178-X",
            customer_email: this.email,
            txref :"MC-1520443531487",
            amount: this.amount,
            currency: "NGN",
        }, {
            headers: {
                'Content-Type': 'application/json',
            }
        }).then(function (response){
            console.log(response)
        })     
    }
  }
}
</script>

<style scoped>

</style>
