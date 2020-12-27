<template>
  <div id="contact">
    <div class="contactCol"></div>
    <div class="contactCol contactForm">
      <b-container>
        <div cols="12" class="contactFormHeader">
          <p>Get in touch with Us</p>
        </div>
        <b-form @submit.prevent="sendInquiry">
          <b-form-group
            label="Name:"
          >
            <b-form-input
              v-model="contactForm.name"
              type="text"
              placeholder="Your name or your business name"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Email:"
          >
            <b-form-input
              v-model="contactForm.email"
              type="email"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Contact Number:"
          >
            <b-form-input
              v-model="contactForm.contact_no"
              type="text"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Preferred mode of communication:"
            v-slot="{ ariaDescribedby }"
          >
            <b-form-radio-group
              id="radio-group-1"
              v-model="contactForm.mode_of_communication"
              :options="mode_of_communications"
              :aria-describedby="ariaDescribedby"
            ></b-form-radio-group>
          </b-form-group>
          <b-form-group
            label="Message:"
          >
            <b-form-textarea
              v-model="contactForm.message"
              rows="3"
              max-rows="6"
            ></b-form-textarea>
          </b-form-group>
          <b-button class="sendBtn" pill>Send</b-button>
        </b-form>
      </b-container>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      contactForm: {
        name: '',
        email: '',
        contact_no: '',
        mode_of_communication: 'Phone',
        message: ''
      },
      mode_of_communications: [
        { text: 'Phone', value: 'Phone' },
        { text: 'Email', value: 'Email' }
      ]
    }
  },
  methods: {
    sendInquiry() {

    }
  }
}
</script>

<style>
  #contact {
    height: 600px;
    width: 100%;
    background-image: url('../../assets/images/contact-background.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
  }

  .contactCol {
    flex: 50%;
  }

  .contactForm {
    background-color: #ffffff;
    height: 600px;
    border-bottom: 16px solid #f26522;
    padding: 20px 20px;
  }

  .contactFormHeader p {
    font-size: 30px;
    color: #88b73d;
    font-weight: 800;
    text-transform: uppercase;
    line-height: 1em;
  }

  .col-form-label, .custom-control-label {
    font-size: 14px;
    font-weight: 700;
  }

  .sendBtn {
    background-color: #f6961e;
    border-color: #f6961e;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 0.1em;
    padding: 8px 20px;
    float: right;
  }

  .sendBtn:hover {
    background-color: #89b83e;
    border-color: #89b83e;
  }

  input[type="text"], input[type="email"], textarea {
    font-size: 14px !important;
    background-color: #ebebeb !important;
  }
</style>
