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
            type="text"
            inputGroup
          >
            <template #prepend>
              <span class="input-group-text inputPoundSymbol">£</span>
            </template>
          </MDBInput>

          <label class="inputLabel btnGroupLabel" for="monthSelection"
            >Loan term (months)</label
          >
          <div name="monthSelection" class="monthBtnGroup">
            <MDBBtn class="monthBtn" color="secondary">12</MDBBtn>
            <MDBBtn class="monthBtn" color="secondary">18</MDBBtn>
            <MDBBtn class="monthBtn" color="secondary">24</MDBBtn>
          </div>
          <MDBBtn class="submitBtn"> Submit </MDBBtn>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { MDBInput, MDBBtn } from "mdb-vue-ui-kit";
export default {
  name: "App",
  components: {
    MDBInput,
    MDBBtn,
  },
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.viewContainer {
  height: 1080px;
  display: flex;
}
.logoBanner {
  display: inline-block;
  width: 356px;
  background: transparent linear-gradient(162deg, #3718b2 0%, #cd33a4 100%) 0%
    0% no-repeat padding-box;
  height: 100%;
  vertical-align: top;
  flex-shrink: 0;
}
.mainSection {
  display: inline-block;
  height: 100%;
  width: 1564px;
  flex-shrink: 0;
}
.formContainer {
  width: 780px;
  margin: 0 auto;
  margin-top: 296px;
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
  width: 250px;
  height: 77px;
  font: normal normal normal 25px/30px Montserrat;
  background: #f2f2f2 0% 0% no-repeat padding-box;
  border: 1px solid #cbcbcb;
  color: #2c2c2c;
}
.inputLabel {
  font: normal normal normal 26px/32px Montserrat;
  color: #6e6e6e;
  margin-bottom: 15px;
}
.btnGroupLabel {
  margin-top: 50px;
}

.submitBtn {
  background: #7600ff 0% 0% no-repeat padding-box;
  border-radius: 5px;
  opacity: 1;
  font: normal normal bold 30px/37px Montserrat;
  color: #ffffff;
  width: 780px;
  height: 77px;
  margin-top: 50px;
  text-transform: unset !important;
}
.submitBtn:hover {
  color: lightgrey !important;
}
.monthBtnGroup {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 7.5px;
}
.logoPlaceholder {
  font: normal normal 900 38px/47px Montserrat;
  top: 44px;
  left: 57px;
  position: relative;
  color: #ffffff;
}

@media (max-width: 375px) {
  .viewContainer {
    height: 851px;
    display: block;
    width: 375px;
  }
  .logoBanner {
    display: block;
    width: 100%;
    height: 51px;
  }
  .logoPlaceholder {
    font: normal normal 900 22px/27px Montserrat;
    top: 12px;
    left: 18px;
  }

  .mainSection {
    width: 375px;
    display: block;
  }
  .formContainer {
    display: block;
    width: 339px;
    margin: auto !important;
    margin-top: 36px !important;
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

  .monthBtn {
    display: block;
    width: 338px;
    height: 60px;
    font: normal normal normal 25px/30px Montserrat;
    margin: 0 auto;
    margin-bottom: 20px;
  }
  .monthBtnGroup {
    display: block;
    margin: 0 auto;
  }
}
</style>
