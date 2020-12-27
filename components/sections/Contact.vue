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
              @input="clearMessage"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Email:"
          >
            <b-form-input
              v-model="contactForm.email"
              type="text"
              @input="clearMessage"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Contact Number:"
          >
            <b-form-input
              v-model="contactForm.contact_no"
              type="text"
              @input="clearMessage"
            ></b-form-input>
          </b-form-group>
          <b-form-group
            label="Preferred mode of communication:"
            v-slot="{ ariaDescribedby }"
          >
            <b-form-radio-group
              id="radio-group-1"
              v-model="contactForm.preferred_mode_of_communication"
              :options="preferred_mode_of_communications"
              :aria-describedby="ariaDescribedby"
              @change="clearMessage"
            ></b-form-radio-group>
          </b-form-group>
          <b-form-group
            label="Message:"
          >
            <b-form-textarea
              v-model="contactForm.message"
              rows="3"
              max-rows="6"
              @input="clearMessage"
            ></b-form-textarea>
          </b-form-group>
          <div class="messageAndButton" :class="[contactFormMessage ? 'space-between' : 'flex-end']">
            <span v-if="contactFormMessage" :class="'text-'+contactFormMessage.color">{{contactFormMessage.message}}</span>
            <b-button type="submit" class="sendBtn" pill>
              <b-icon v-if="isSubmitting" icon="arrow-clockwise" animation="spin"></b-icon>
              <span v-else>Send</span>
            </b-button>
          </div>
        </b-form>
      </b-container>
    </div>
  </div>
</template>

<script>
import { BIcon, BIconArrowClockwise } from 'bootstrap-vue'

export default {
  name: 'Contact',
  components: {
    BIcon,
    BIconArrowClockwise
  },
  data() {
    return {
      contactForm: {
        name: '',
        email: '',
        contact_no: '',
        preferred_mode_of_communication: 'Phone',
        message: ''
      },
      preferred_mode_of_communications: [
        { text: 'Phone', value: 'Phone' },
        { text: 'Email', value: 'Email' }
      ],
      contactFormMessage: null,
      isSubmitting: false
    }
  },
  methods: {
    encode(data) {
      return Object.keys(data).map(key =>
        `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
      ).join('&')
    },
    clearMessage() {
      this.contactFormMessage = null
    },
    resetFields() {
      Object.keys(this.contactForm).map(key => {
        if(key != 'preferred_mode_of_communication') {
          this.contactForm[key] = ''
        } else {
          this.contactForm[key] = 'Phone'
        }
      })
    },
    sendInquiry() {
      this.isSubmitting = true
      axios.post('/', this.encode({ 'form-name': 'inquiries', ...this.contactForm }), { headers: { 'Content-Type': 'application/x-www-form-urlencoded'  } })
      .then(() => {
        this.isSubmitting = false
        this.contactFormMessage = { color: 'success', message: 'Message was submitted. We will get back to you on your preferred mode of communication. Thank you for reaching out!' }
        this.resetFields()
      })
      .catch(err => {
        console.log(err)
        this.isSubmitting = false
        this.contactFormMessage = { color: 'danger', message: 'There was an error submitting your message.' }
      })
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

  .messageAndButton {
    display: flex;
  }

  .messageAndButton span {
    font-size: 13px;
    font-weight: 600;
  }

  .flex-end {
    justify-content: flex-end;
  }

  .space-between {
    justify-content: space-between;
  }

  .sendBtn {
    background-color: #f6961e;
    border-color: #f6961e;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 0.1em;
    padding: 8px 20px;
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
