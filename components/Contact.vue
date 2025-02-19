<!-- App.vue -->
<template>
  <!-- Hidden static form for Netlify detection -->
  <div>
    <form name="contact-codeg" netlify hidden>
    <input type="text" name="first-name" />
    <input type="text" name="last-name" />
    <input type="email" name="email" />
    <input type="tel" name="phone-number" />
    <textarea name="message"></textarea>
  </form>

  <!-- Main content -->
  <div class="relative isolate bg-white">
    <div class="mx-auto grid max-w-7xl grid-cols-1 lg:grid-cols-2">
      <!-- Contact Information Section -->
      <div class="relative px-6 pt-24 pb-20 sm:pt-32 lg:static lg:px-8 lg:py-48">
        <div class="mx-auto max-w-xl lg:mx-0 lg:max-w-lg">
          <div class="flex flex-col space-y-3">
            <span class="text-sm font-semibold leading-6 text-indigo-600">Contacto</span>
            <h2 class="text-4xl font-semibold tracking-tight text-gray-900">Conecta con Nosotros</h2>
          </div>
          <p class="mt-6 text-lg/8 text-gray-600">
            ¿Interesado en ser parte de CODEG? Estamos aquí para responder tus preguntas y ayudarte a formar parte de nuestra comunidad de líderes.
          </p>
          <!-- (Additional contact info omitted for brevity) -->
        </div>
      </div>

      <!-- Contact Form Section -->
      <form
        name="contact-codeg"
        method="POST"
        data-netlify="true"
        @submit.prevent="handleSubmit"
        class="px-6 pt-20 pb-24 sm:pb-32 lg:px-8 lg:py-48"
      >
        <!-- Hidden input for Netlify Forms (must match the form name) -->
        <input type="hidden" name="form-name" value="contact-codeg" />

        <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
          <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
            <!-- First Name -->
            <div>
              <label for="first-name" class="block text-sm/6 font-semibold text-gray-900">Nombre</label>
              <div class="mt-2.5">
                <input
                  type="text"
                  name="first-name"
                  id="first-name"
                  v-model="formData.firstName"
                  required
                  autocomplete="given-name"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                />
              </div>
            </div>

            <!-- Last Name -->
            <div>
              <label for="last-name" class="block text-sm/6 font-semibold text-gray-900">Apellido</label>
              <div class="mt-2.5">
                <input
                  type="text"
                  name="last-name"
                  id="last-name"
                  v-model="formData.lastName"
                  required
                  autocomplete="family-name"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                />
              </div>
            </div>

            <!-- Email -->
            <div class="sm:col-span-2">
              <label for="email" class="block text-sm/6 font-semibold text-gray-900">Correo electrónico</label>
              <div class="mt-2.5">
                <input
                  type="email"
                  name="email"
                  id="email"
                  v-model="formData.email"
                  required
                  autocomplete="email"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                />
              </div>
            </div>

            <!-- Phone Number -->
            <div class="sm:col-span-2">
              <label for="phone-number" class="block text-sm/6 font-semibold text-gray-900">Teléfono</label>
              <div class="mt-2.5">
                <input
                  type="tel"
                  name="phone-number"
                  id="phone-number"
                  v-model="formData.phone"
                  required
                  autocomplete="tel"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                />
              </div>
            </div>

            <!-- Message -->
            <div class="sm:col-span-2">
              <label for="message" class="block text-sm/6 font-semibold text-gray-900">Mensaje</label>
              <div class="mt-2.5">
                <textarea
                  name="message"
                  id="message"
                  v-model="formData.message"
                  required
                  rows="4"
                  placeholder="¿En qué podemos ayudarte?"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                ></textarea>
              </div>
            </div>
          </div>

          <div class="mt-8 flex justify-end">
            <button
              type="submit"
              :disabled="isSubmitting"
              class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 disabled:bg-indigo-300"
            >
              {{ isSubmitting ? 'Enviando...' : 'Enviar mensaje' }}
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { BuildingOffice2Icon, EnvelopeIcon, PhoneIcon } from '@heroicons/vue/24/outline'

const isSubmitting = ref(false)
const formData = ref({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  message: ''
})

const handleSubmit = async (e) => {
  try {
    isSubmitting.value = true
    const formElement = e.target
    // Create a FormData object from the form element
    const payload = new FormData(formElement)

    // Send the AJAX POST request to Netlify
    await fetch('/', {
      method: 'POST',
      headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
      body: new URLSearchParams(payload).toString(),
    })

    // Reset the reactive form data (clearing the input fields)
    formData.value = {
      firstName: '',
      lastName: '',
      email: '',
      phone: '',
      message: ''
    }
    
    alert('Mensaje enviado con éxito. Nos pondremos en contacto contigo pronto.')
  } catch (error) {
    console.error('Error:', error)
    alert('Hubo un error al enviar el mensaje. Por favor, intenta de nuevo.')
  } finally {
    isSubmitting.value = false
  }
}
</script>