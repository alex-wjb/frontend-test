<template>
  <div class="viewContainer">
    <div class="logoBanner">
      <p class="logoPlaceholder">Logo.</p>
    </div>

    <div class="mainSection">
      <div class="formContainer">
        <p class="formTitle">
          Apply for a loan now
          <img src="./assets/thumbs-up.png" alt="" class="thumbImg" />
        </p>

        <form action="">
          <label class="inputLabel" for="loanAmount">Loan amount</label>

          <MDBInput
            name="loanAmount"
            class="amountInput"
            type="number"
            inputGroup
            v-model="loanAmount"
          >
            <template #prepend>
              <span class="input-group-text inputPoundSymbol">£</span>
            </template>
          </MDBInput>
          <p class="errorMsg" v-if="loanReqErr">Please enter a loan amount</p>
          <label class="inputLabel btnGroupLabel" for="monthSelection"
            >Loan term (months)</label
          >

          <div name="monthSelection" class="monthBtnGroup">
            <MDBBtn
              class="monthBtn"
              :class="{ active: loanTerm == 12 }"
              color="secondary"
              @click="setLoanTerm(12)"
              >12</MDBBtn
            >
            <MDBBtn
              class="monthBtn"
              color="secondary"
              :class="{ active: loanTerm == 18 }"
              @click="setLoanTerm(18)"
              >18</MDBBtn
            >
            <MDBBtn
              class="monthBtn"
              color="secondary"
              :class="{ active: loanTerm == 24 }"
              @click="setLoanTerm(24)"
              >24</MDBBtn
            >
          </div>
          <p class="errorMsg" v-if="termReqErr">Please select a loan term</p>
          <MDBBtn class="submitBtn" @click="submitData"> Submit </MDBBtn>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { MDBInput, MDBBtn } from "mdb-vue-ui-kit";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    MDBInput,
    MDBBtn,
  },
  setup() {
    const loanAmount = ref(null);
    const loanTerm = ref(null);
    const loanReqErr = ref(false);
    const termReqErr = ref(false);

    //returns true if required inputs are empty
    const checkRequired = () => {
      loanReqErr.value = false;
      termReqErr.value = false;
      let required = false;
      if (loanAmount.value == null || loanAmount.value == "") {
        loanReqErr.value = true;
        required = true;
      }
      if (loanTerm.value == null) {
        termReqErr.value = true;
        required = true;
      }
      return required;
    };
    //replace with code to send to backend via POST etc.
    const submitData = () => {
      if (checkRequired()) return;
      alert(
        "You have selected a loan of £" +
          loanAmount.value +
          " for " +
          loanTerm.value +
          " months."
      );
    };

    const setLoanTerm = (n) => {
      loanTerm.value = n;
    };
    return {
      loanAmount,
      checkRequired,
      loanReqErr,
      loanTerm,
      setLoanTerm,
      termReqErr,
      submitData,
    };
  },
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
}

.viewContainer {
  width: 100%;
  height: 100%;
  /* removes whitespace from inline block elements */
  display: flex;
}
.logoBanner {
  min-height: 100vh;
  background: transparent linear-gradient(162deg, #3718b2 0%, #cd33a4 100%) 0%
    0% no-repeat padding-box;
  vertical-align: top;
  flex-shrink: 1;
  min-width: 200px;
  max-width: 356px;
  flex-grow: 1;
}
.mainSection {
  /* flex-shrink: 0; */
  flex-grow: 1;
}
.formContainer {
  display: block;
  width: 780px;
  margin: 0 auto;
  margin-top: 296px;
  padding-bottom: 279px;
}
.formTitle {
  font: normal normal bold 44px/54px Montserrat;
  display: inline-block;
  margin-bottom: 26px;
}
.thumbImg {
  display: inline-block;
  width: 66px;
  height: 74px;
  vertical-align: text-bottom;
}
.amountInput {
  height: 78px !important;
  margin: 0px !important;
  font: normal normal normal 35px/43px Montserrat;
}
.inputPoundSymbol {
  height: 78px;
  border: none;
  font: normal normal bold 35px/43px Montserrat;
}
.monthBtn {
  height: 70px;
  margin-left: 15px;
  min-width: 250px;
  margin-right: -4px;
  display: inline-block;
  font: normal normal normal 25px/30px Montserrat;
  background: #f2f2f2 0% 0% no-repeat padding-box;
  border: 1px solid #cbcbcb;
  color: #2c2c2c;
  margin-bottom: 20px !important;
}
.monthBtnGroup button:first-child {
  margin-left: 0px;
}
.monthBtnGroup {
  width: 100%;
  text-align: center;
}
.inputLabel {
  font: normal normal normal 26px/32px Montserrat;
  color: #6e6e6e;
  margin-bottom: 15px;
}
.btnGroupLabel {
  margin-top: 50px;
  display: block;
}

.submitBtn {
  display: block;
  background: #7600ff 0% 0% no-repeat padding-box;
  border-radius: 5px;
  opacity: 1;
  font: normal normal bold 30px/37px Montserrat;
  color: #ffffff;
  width: 780px;
  height: 77px;
  margin: auto;
  margin-top: 70px;
  text-transform: unset !important;
}
.submitBtn:hover {
  color: lightgrey !important;
}

.logoPlaceholder {
  font: normal normal 900 38px/47px Montserrat;
  top: 44px;
  left: 57px;
  position: relative;
  color: #ffffff;
}

.errorMsg {
  margin-top: 5px;
  color: #ef5350;
  font: normal normal normal 26px/32px Montserrat;
}

@media (max-width: 1100px) {
  .formContainer {
    width: 500px;
    margin: 0 auto;
    margin-top: 150px;
    padding-bottom: 150px;
  }
  .logoBanner {
    max-width: 200px;
  }
  .monthBtn {
    height: 70px;
    min-width: 338px;
    margin: 0 auto;
    display: block;
  }
  .formTitle {
    width: 110%;
  }
  .monthBtnGroup button:first-child {
    margin: 0 auto;
  }
  .monthBtnGroup {
    width: 100%;
    text-align: left;
  }
  .submitBtn {
    width: 338px;
  }
  .thumbImg {
    width: 45px;
    height: 51px;
  }
}

@media (max-width: 850px) {
  .viewContainer {
    height: 100%;
    display: flex;
    flex-wrap: wrap;
  }
  .logoBanner {
    width: 100%;
    min-height: 51px;
    max-width: none;
  }
  .logoPlaceholder {
    font: normal normal 900 22px/27px Montserrat;
    top: 12px;
    left: 18px;
    width: fit-content;
  }

  .mainSection {
    width: 100%;
  }
  .formContainer {
    display: block;
    width: 339px;
    margin: auto !important;
    margin-top: 36px !important;
    padding-bottom: 139px;
  }
  .formTitle {
    font: normal normal bold 43px/53px Montserrat;
    width: 338px;
    height: 106px;
    margin: 0 auto;
    margin-bottom: 27px;
  }
  .thumbImg {
    display: inline-block;
    width: 45px;
    height: 51px;
    vertical-align: text-bottom;
  }
  .amountInput {
    height: 60px;
    margin-bottom: 50px;
  }
  .inputPoundSymbol {
    height: 80px;
    border: none;
    font: normal normal bold 35px/43px Montserrat;
  }

  .inputLabel {
    font: normal normal normal 18px/22px Montserrat;
    margin-bottom: 12px;
  }
  .btnGroupLabel {
    margin-top: 50px;
  }

  .submitBtn {
    display: block;
    font: normal normal bold 22px/27px Montserrat;
    width: 339px;
    height: 60px;
    margin-top: 40px !important;
    margin: 0 auto;
  }

  .monthBtnGroup button:first-child {
    margin-left: 0;
  }
  .monthBtn {
    display: block;
    width: 338px;
    height: 60px;
    font: normal normal normal 25px/30px Montserrat;
    margin-bottom: 20px !important;
  }

  .monthBtnGroup {
    text-align: left;
    display: block;
    margin: 0 auto;
    width: 100%;
  }

  .errorMsg {
    margin-top: 5px;
    color: #ef5350;
    font: normal normal normal 18px/22px Montserrat;
  }
}
</style>
