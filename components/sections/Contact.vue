<template>
  <div id="contact">
    <div class="contactBackground"></div>
    <div class="contactForm">
      <b-container>
        <div cols="12" class="contactFormHeader">
          <p>Get in touch with Us</p>
        </div>
        <b-form name="inquiries" @submit.prevent="sendInquiry" data-netlify="true" data-netlify-honeypot="bot-field" method="POST" action="/contact">
          <input type="hidden" name="form-name" value="inquiries" />
          <b-form-group
            label="Name:"
          >
            <b-form-input
              v-model="$v.contactForm.name.$model"
              type="text"
              name="name"
              placeholder="Your name or your business name"
              @input="clearMessage"
              :state="validateInput('name')"
              aria-describedby="nameError"
            ></b-form-input>
            <b-form-invalid-feedback id="nameError">Name is required.</b-form-invalid-feedback>
          </b-form-group>
          <b-form-group
            label="Email:"
          >
            <b-form-input
              v-model="$v.contactForm.email.$model"
              type="text"
              name="email"
              @input="clearMessage"
              :state="validateInput('email')"
              aria-describedby="emailError"
            ></b-form-input>
            <b-form-invalid-feedback id="emailError">Email is required and must be valid.</b-form-invalid-feedback>
          </b-form-group>
          <b-form-group
            label="Contact Number:"
          >
            <b-form-input
              v-model="$v.contactForm.contact_no.$model"
              type="text"
              name="contact_no"
              @input="clearMessage"
              :state="validateInput('contact_no')"
              aria-describedby="contactNoError"
            ></b-form-input>
            <b-form-invalid-feedback id="contactNoError">Contact number is required.</b-form-invalid-feedback>
          </b-form-group>
          <b-form-group
            label="Preferred mode of communication:"
            v-slot="{ ariaDescribedby }"
          >
            <b-form-radio-group
              id="radio-group-1"
              v-model="$v.contactForm.mode_of_communication.$model"
              :options="mode_of_communications"
              :aria-describedby="ariaDescribedby"
              name="preferred_mode_of_communication"
              @change="clearMessage"
              :state="validateInput('mode_of_communication')"
            >
              <b-form-invalid-feedback :state="validateInput('mode_of_communication')">Please choose a preferred mode of communication.</b-form-invalid-feedback>
            </b-form-radio-group>
          </b-form-group>
          <b-form-group
            label="Message:"
          >
            <b-form-textarea
              v-model="$v.contactForm.message.$model"
              rows="3"
              max-rows="6"
              name="message"
              @input="clearMessage"
              :state="validateInput('message')"
              aria-describedby="messageError"
            ></b-form-textarea>
            <b-form-invalid-feedback id="messageError">Message is required.</b-form-invalid-feedback>
          </b-form-group>
          <div class="contactFormMessage">
            <span v-if="contactFormMessage" :class="'text-'+contactFormMessage.color">{{contactFormMessage.message}}</span>
          </div>
          <div class="contactFormButton">
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
import { required, email } from 'vuelidate/lib/validators'

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
        mode_of_communication: 'Phone',
        message: ''
      },
      mode_of_communications: [
        { text: 'Phone', value: 'Phone' },
        { text: 'Email', value: 'Email' }
      ],
      contactFormMessage: null,
      isSubmitting: false
    }
  },
  validations: {
    contactForm: {
      name: { required },
      email: { required, email },
      contact_no: { required },
      mode_of_communication: { required },
      message: { required }
    }
  },
  methods: {
    validateInput(input) {
      const { $dirty, $error } = this.$v.contactForm[input]
      return $dirty ? !$error : null
    },
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
        if(key != 'mode_of_communication') {
          this.contactForm[key] = ''
        } else {
          this.contactForm[key] = 'Phone'
        }
      })
    },
    sendInquiry() {
      if(!this.$v.contactForm.$invalid) {
        this.isSubmitting = true
        this.$axios.post('/contact', this.encode({ 'form-name': 'inquiries', ...this.contactForm }), { headers: { 'Content-Type': 'application/x-www-form-urlencoded'  } })
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
      } else {
        this.$v.contactForm.$touch()
      }
    }
  }
}
</script>

<style>
  #contact {
    height: 100%;
    width: 100%;
    background-image: url('../../assets/images/contact-background.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
  }

  .contactBackground, .contactForm {
    flex: 50%;
  }

  .contactForm {
    background-color: #ffffff;
    height: 100%;
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

  .contactFormMessage {
    display: flex;
    justify-content: flex-start;
    margin-bottom: 10px;
  }

  .contactFormMessage span {
    font-size: 13px;
    font-weight: 600;
  }

  .contactFormButton {
    display: flex;
    justify-content: flex-end;
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

  input, textarea {
    font-size: 14px !important;
    background-color: #ebebeb !important;
  }

  .invalid-feedback {
    font-weight: 600;
  }

  @media screen and (max-width: 767px) {
    .contactBackground {
      flex: 30%;
    }

    .contactForm {
      flex: 70%;
    }
  }

  @media screen and (max-width: 480px) {
    .contactBackground {
      display: none;
    }

    .contactForm {
      flex: 100%;
    }
  }
</style>
