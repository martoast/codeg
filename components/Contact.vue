<template>
  <div class="relative isolate bg-white">
    <div class="mx-auto grid max-w-7xl grid-cols-1 lg:grid-cols-2">
      <!-- Contact Information Section -->
      <div class="relative px-6 pt-24 pb-20 sm:pt-32 lg:static lg:px-8 lg:py-48">
        <div class="mx-auto max-w-xl lg:mx-0 lg:max-w-lg">
          <div class="absolute inset-y-0 left-0 -z-10 w-full overflow-hidden bg-gray-100 ring-1 ring-gray-900/10 lg:w-1/2">
            <svg class="absolute inset-0 size-full stroke-gray-200 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]" aria-hidden="true">
              <defs>
                <pattern id="83fd4e5a-9d52-42fc-97b6-718e5d7ee527" width="200" height="200" x="100%" y="-1" patternUnits="userSpaceOnUse">
                  <path d="M130 200V.5M.5 .5H200" fill="none" />
                </pattern>
              </defs>
              <rect width="100%" height="100%" stroke-width="0" fill="white" />
              <svg x="100%" y="-1" class="overflow-visible fill-gray-50">
                <path d="M-470.5 0h201v201h-201Z" stroke-width="0" />
              </svg>
              <rect width="100%" height="100%" stroke-width="0" fill="url(#83fd4e5a-9d52-42fc-97b6-718e5d7ee527)" />
            </svg>
          </div>
          <h2 class="text-4xl font-semibold tracking-tight text-pretty text-gray-900 sm:text-5xl">Get in touch</h2>
          <p class="mt-6 text-lg/8 text-gray-600">
            Proin volutpat consequat porttitor cras nullam gravida at. Orci molestie a eu arcu. Sed ut tincidunt integer elementum id sem. Arcu sed malesuada et magna.
          </p>
          <dl class="mt-10 space-y-4 text-base/7 text-gray-600">
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Address</span>
                <BuildingOffice2Icon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>545 Mavis Island<br />Chicago, IL 99191</dd>
            </div>
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Telephone</span>
                <PhoneIcon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <a class="hover:text-gray-900" href="tel:+1 (555) 234-5678">+1 (555) 234-5678</a>
              </dd>
            </div>
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Email</span>
                <EnvelopeIcon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <a class="hover:text-gray-900" href="mailto:hello@example.com">hello@example.com</a>
              </dd>
            </div>
          </dl>
        </div>
      </div>

      <!-- Contact Form Section -->
      <form
        name="contact-codeg"
        method="POST"
        action="/thanks"
        data-netlify="true"
        netlify-honeypot="bot-field"
        @submit="handleSubmit($event)"
        class="px-6 pt-20 pb-24 sm:pb-32 lg:px-8 lg:py-48"
      >
        <!-- Hidden input for Netlify -->
        <input type="hidden" name="form-name" value="contact-codeg" />
        <!-- Honeypot field -->
        <p hidden>
          <label>
            Don’t fill this out:
            <input name="bot-field" />
          </label>
        </p>
        <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
          <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
            <!-- First Name -->
            <div>
              <label for="first-name" class="block text-sm font-semibold text-gray-900">Nombre</label>
              <div class="mt-2.5">
                <input
                  type="text"
                  name="first-name"
                  id="first-name"
                  v-model="formData.firstName"
                  required
                  autocomplete="given-name"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm"
                />
                <p v-if="firstNameError" class="text-red-500 text-sm">{{ firstNameError }}</p>
              </div>
            </div>

            <!-- Last Name -->
            <div>
              <label for="last-name" class="block text-sm font-semibold text-gray-900">Apellido</label>
              <div class="mt-2.5">
                <input
                  type="text"
                  name="last-name"
                  id="last-name"
                  v-model="formData.lastName"
                  required
                  autocomplete="family-name"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm"
                />
                <p v-if="lastNameError" class="text-red-500 text-sm">{{ lastNameError }}</p>
              </div>
            </div>

            <!-- Email -->
            <div class="sm:col-span-2">
              <label for="email" class="block text-sm font-semibold text-gray-900">Correo electrónico</label>
              <div class="mt-2.5">
                <input
                  type="email"
                  name="email"
                  id="email"
                  v-model="formData.email"
                  required
                  autocomplete="email"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm"
                />
                <p v-if="emailError" class="text-red-500 text-sm">{{ emailError }}</p>
              </div>
            </div>

            <!-- Phone Number -->
            <div class="sm:col-span-2">
              <label for="phone-number" class="block text-sm font-semibold text-gray-900">Teléfono</label>
              <div class="mt-2.5">
                <input
                  type="tel"
                  name="phone-number"
                  id="phone-number"
                  v-model="formData.phone"
                  required
                  autocomplete="tel"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm"
                />
                <p v-if="phoneError" class="text-red-500 text-sm">{{ phoneError }}</p>
              </div>
            </div>

            <!-- Message -->
            <div class="sm:col-span-2">
              <label for="message" class="block text-sm font-semibold text-gray-900">Mensaje</label>
              <div class="mt-2.5">
                <textarea
                  name="message"
                  id="message"
                  v-model="formData.message"
                  required
                  rows="4"
                  placeholder="¿En qué podemos ayudarte?"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm"
                ></textarea>
                <p v-if="messageError" class="text-red-500 text-sm">{{ messageError }}</p>
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
</template>

<script setup>
import { ref, computed } from 'vue'
import { BuildingOffice2Icon, EnvelopeIcon, PhoneIcon } from '@heroicons/vue/24/outline'

// Reactive form data
const formData = ref({
  firstName: '',
  lastName: '',
  email: '',
  phone: '',
  message: ''
})

// Submission flag
const isSubmitting = ref(false)

// Computed validations
const firstNameError = computed(() => {
  if (!formData.value.firstName.trim()) return 'El nombre es requerido.'
  return ''
})
const lastNameError = computed(() => {
  if (!formData.value.lastName.trim()) return 'El apellido es requerido.'
  return ''
})
const emailError = computed(() => {
  if (!formData.value.email.trim()) return 'El correo es requerido.'
  const emailRegex = /\S+@\S+\.\S+/
  if (!emailRegex.test(formData.value.email)) return 'Por favor, ingresa un correo válido.'
  return ''
})
const phoneError = computed(() => {
  if (!formData.value.phone.trim()) return 'El teléfono es requerido.'
  return ''
})
const messageError = computed(() => {
  if (!formData.value.message.trim()) return 'El mensaje es requerido.'
  return ''
})

// Overall form validity
const formValid = computed(() => {
  return (
    !firstNameError.value &&
    !lastNameError.value &&
    !emailError.value &&
    !phoneError.value &&
    !messageError.value
  )
})

// Submit handler – if form is invalid, prevent native submission
const handleSubmit = (e) => {
  if (!formValid.value) {
    e.preventDefault()
    alert('Por favor corrige los errores antes de enviar el formulario.')
  }
  // Otherwise, allow native submission so Netlify processes it
}
</script>

<style scoped>
/* Additional custom styling if needed */
</style>
