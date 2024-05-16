<template>
  <div class="contact-form-container">
    <h2 id="form-heading">Contáctanos</h2>
    <form @submit.prevent="submitForm" class="contact-form" aria-labelledby="form-heading">
      <div class="form-group">
        <label for="name" class="form-label">Nombre *</label>
        <input
          type="text"
          id="name"
          v-model="form.name"
          required
          class="form-input"
          aria-required="true"
          aria-describedby="name-info"
        />
        <div id="name-info" class="form-info">Por favor, ingrese su nombre completo.</div>
      </div>
      <div class="form-group">
        <label for="email" class="form-label">Correo electrónico *</label>
        <input
          type="email"
          id="email"
          v-model="form.email"
          required
          class="form-input"
          aria-required="true"
          aria-describedby="email-info"
        />
        <div id="email-info" class="form-info">
          Por favor, ingrese una dirección de correo electrónico válida.
        </div>
      </div>
      <div class="form-group">
        <label for="phone" class="form-label">Teléfono *</label>
        <input
          type="tel"
          id="phone"
          v-model="form.phone"
          required
          class="form-input"
          aria-required="true"
          aria-describedby="phone-info"
        />
        <div id="phone-info" class="form-info">
          Por favor, ingrese un número de teléfono válido.
        </div>
      </div>
      <div class="form-group">
        <label for="message" class="form-label">Mensaje *</label>
        <textarea
          id="message"
          v-model="form.message"
          required
          class="form-input"
          aria-required="true"
          aria-describedby="message-info"
        ></textarea>
        <div id="message-info" class="form-info">Por favor, ingrese su mensaje.</div>
      </div>
      <div class="form-group">
        <label for="property" class="form-label">Propiedad de interés *</label>
        <select
          id="property"
          v-model="form.property"
          required
          class="form-input"
          aria-required="true"
          aria-describedby="property-info"
        >
          <option value="">Selecciona una propiedad</option>
          <option v-for="(property, index) in properties" :value="property" :key="index">
            {{ property }}
          </option>
        </select>
        <div id="property-info" class="form-info">
          Por favor, seleccione una propiedad de interés.
        </div>
      </div>
      <div class="form-group">
        <label for="checkbox" class="form-label">
          <input
            class="form-checkbox"
            type="checkbox"
            id="checkbox"
            v-model="form.newsletter"
            aria-describedby="newsletter-info"
          />
          Suscribirme al boletín
          <div id="newsletter-info" class="form-info">
            Reciba noticias y actualizaciones sobre nuestras propiedades.
          </div>
        </label>
      </div>
      <div class="form-group">
        <label for="image" class="form-label">Subir una imagen (opcional)</label>
        <input
          type="file"
          id="image"
          @change="handleImageUpload"
          class="form-input"
          aria-describedby="image-info"
        />
        <div id="image-info" class="form-info">
          Puede subir una imagen relacionada con su consulta.
        </div>
      </div>
      <button type="submit" class="submit-btn">Enviar</button>
    </form>
    <div v-if="showSuccessMessage" class="success-message" role="alert" aria-live="polite">
      <p>¡Gracias por tu envío!</p>
    </div>
  </div>
</template>
<style scoped>
.contact-form-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fad9a6;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.contact-form-container h2 {
  text-align: center;
  margin-bottom: 20px;
  color: #142433;
}

.form-group {
  margin-bottom: 20px;
}

.form-label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
  color: #295264;
}

.form-input {
  width: 100%;
  padding: 10px;
  border: 1px solid #295264;
  border-radius: 4px;
  font-size: 16px;
  background-color: #fff;
}

.form-info {
  font-size: 14px;
  color: #89373d;
  margin-top: 5px;
}

.form-checkbox label {
  display: flex;
  align-items: center;
  color: #142433;
}

.form-checkbox input[type='checkbox'] {
  margin-right: 10px;
}

.submit-btn {
  display: block;
  width: 100%;
  padding: 10px;
  background-color: #89373d;
  color: #fff;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.submit-btn:hover {
  background-color: #bd2f28;
}

.success-message {
  margin-top: 20px;
  padding: 10px;
  background-color: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
  border-radius: 4px;
  text-align: center;
}
</style>
<script>
export default {
  data() {
    return {
      form: {
        name: '',
        email: '',
        phone: '',
        message: '',
        property: '',
        newsletter: false,
        image: null
      },
      properties: [
        'Mansión de Lujo en la Costa',
        'Lujosa Villa Costera',
        'Chalet de Montaña Acogedor',
        'Residencia Urbana Vanguardista'
      ],
      showSuccessMessage: false
    }
  },
  methods: {
    submitForm() {
      if (this.validateForm()) {
        // Handle form submission logic here
        console.log('Formulario enviado:', this.form)
        this.showSuccessMessage = true
      }
    },
    validateForm() {
      const { name, email, phone, message, property } = this.form
      if (!name || !email || !phone || !message || !property) {
        alert('Por favor complete todos los campos requeridos para continuar.')
        return false
      }
      return true
    },
    handleImageUpload(event) {
      this.form.image = event.target.files[0]
    }
  }
}
</script>
