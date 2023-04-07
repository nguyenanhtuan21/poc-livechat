<template>
  <div class="greetings">
    Tạo một button trên livechat
    <button @click="createConnectionHelpDesk">Test mình đi</button>
  </div>
</template>
<script>
import * as CustomerSDK from "@livechat/customer-sdk";
import * as HelpDesk from "@livechat/helpdesk-sdk";
export default {
  data() {
    return {
      user: null,
    };
  },
  methods: {
    createConnectionTicket() {
      const TOKEN = "dal:MDwUwBSgRpZavVgDU3PVwULDrNE";
      const BASE64TOKEN =
        "NTIyZDA1NmItMDRkYS00ZDQ5LWJjNmEtY2YxMTU2ZjA1ZmFlOmRhbDpNRHdVd0JTZ1JwWmF2VmdEVTNQVndVTERyTkU=";
      console.log(this.test);
      const LICENSE_ID = 14037057;
      const CLIENT_ID = "10a0d0a52a3d1dbcc63906eb5c6e9198";
      const CLIENT_SECRET = "17c9b6fb48de3c3a3d639b7cd7bcbb66d9a1e6bb";
      const customerSDK = CustomerSDK.init({
        licenseId: LICENSE_ID,
        clientId: CLIENT_ID,
        autoConnect: false,
      });
      customerSDK.connect();
      customerSDK
        .getCustomer()
        .then((customer) => {
          console.log(customer);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    createConnectionHelpDesk() {
      console.log(`Created a ticket with id:`);
      HelpDesk.createDetailsWidget().then((widget) => {
        console.log("test");
        console.log(widget);
      });
    },
  },
  created() {
    // this.createConnection();
  },
};
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
