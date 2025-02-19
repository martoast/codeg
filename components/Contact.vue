<template>
  <div class="relative isolate bg-white">
    <div class="mx-auto grid max-w-7xl grid-cols-1 lg:grid-cols-2">
      <!-- Contact Information Section -->
      <div class="relative px-6 pt-24 pb-20 sm:pt-32 lg:static lg:px-8 lg:py-48">
        <div class="mx-auto max-w-xl lg:mx-0 lg:max-w-lg">
          <div class="absolute inset-y-0 left-0 -z-10 w-full overflow-hidden bg-gray-100 ring-1 ring-gray-900/10 lg:w-1/2">
            <svg
              class="absolute inset-0 size-full stroke-gray-200 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]"
              aria-hidden="true"
            >
              <defs>
                <pattern
                  id="83fd4e5a-9d52-42fc-97b6-718e5d7ee527"
                  width="200"
                  height="200"
                  x="100%"
                  y="-1"
                  patternUnits="userSpaceOnUse"
                >
                  <path d="M130 200V.5M.5 .5H200" fill="none" />
                </pattern>
              </defs>
              <rect width="100%" height="100%" stroke-width="0" fill="white" />
              <svg x="100%" y="-1" class="overflow-visible fill-gray-50">
                <path d="M-470.5 0h201v201h-201Z" stroke-width="0" />
              </svg>
              <rect
                width="100%"
                height="100%"
                stroke-width="0"
                fill="url(#83fd4e5a-9d52-42fc-97b6-718e5d7ee527)"
              />
            </svg>
          </div>
          <div class="flex flex-col space-y-3">
            <span class="text-sm font-semibold leading-6 text-indigo-600">Contacto</span>
            <h2 class="text-4xl font-semibold tracking-tight text-gray-900">Conecta con Nosotros</h2>
          </div>
          <p class="mt-6 text-lg/8 text-gray-600">
            ¿Interesado en ser parte de CODEG? Estamos aquí para responder tus preguntas y ayudarte a formar parte de nuestra comunidad de líderes.
          </p>
          <dl class="mt-10 space-y-4 text-base/7 text-gray-600">
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Dirección</span>
                <BuildingOffice2Icon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                Tijuana, Baja California<br />México
              </dd>
            </div>
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Teléfono</span>
                <PhoneIcon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <a class="hover:text-gray-900" href="tel:+52 686 234 5678">+52 686 234 5678</a>
              </dd>
            </div>
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Correo</span>
                <EnvelopeIcon class="h-7 w-6 text-gray-400" aria-hidden="true" />
              </dt>
              <dd>
                <a class="hover:text-gray-900" href="mailto:contacto@codeg.mx">contacto@codeg.mx</a>
              </dd>
            </div>
            <div class="flex gap-x-4">
              <dt class="flex-none">
                <span class="sr-only">Instagram</span>
                <svg class="h-7 w-6 text-gray-400" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    fill-rule="evenodd"
                    d="M12.315 2c2.43 0 2.784.013 3.808.06 1.064.049 1.791.218 2.427.465a4.902 4.902 0 011.772 1.153 4.902 4.902 0 011.153 1.772c.247.636.416 1.363.465 2.427.048 1.067.06 1.407.06 4.123v.08c0 2.643-.012 2.987-.06 4.043-.049 1.064-.218 1.791-.465 2.427a4.902 4.902 0 01-1.153 1.772 4.902 4.902 0 01-1.772 1.153c-.636.247-1.363.416-2.427.465-1.067.048-1.407.06-4.123.06h-.08c-2.643 0-2.987-.012-4.043-.06-1.064-.049-1.791-.218-2.427-.465a4.902 4.902 0 01-1.772-1.153 4.902 4.902 0 01-1.153-1.772c-.247-.636-.416-1.363-.465-2.427-.047-1.024-.06-1.379-.06-3.808v-.63c0-2.43.013-2.784.06-3.808.049-1.064.218-1.791.465-2.427a4.902 4.902 0 011.153-1.772A4.902 4.902 0 015.45 2.525c.636-.247 1.363-.416 2.427-.465C8.901 2.013 9.256 2 11.685 2h.63zm-.081 1.802h-.468c-2.456 0-2.784.011-3.807.058-.975.045-1.504.207-1.857.344-.467.182-.8.398-1.15.748-.35.35-.566.683-.748 1.15-.137.353-.3.882-.344 1.857-.047 1.023-.058 1.351-.058 3.807v.468c0 2.456.011 2.784.058 3.807.045.975.207 1.504.344 1.857.182.466.399.8.748 1.15.35.35.683.566 1.15.748.353.137.882.3 1.857.344 1.054.048 1.37.058 4.041.058h.08c2.597 0 2.917-.01 3.96-.058.976-.045 1.505-.207 1.858-.344.466-.182.8-.398 1.15-.748.35-.35.566-.683.748-1.15.137-.353.3-.882.344-1.857.048-1.055.058-1.37.058-4.041v-.08c0-2.597-.01-2.917-.058-3.96-.045-.976-.207-1.505-.344-1.858a3.097 3.097 0 00-.748-1.15 3.098 3.098 0 00-1.15-.748c-.353-.137-.882-.3-1.857-.344-1.023-.047-1.351-.058-3.807-.058zM12 6.865a5.135 5.135 0 110 10.27 5.135 5.135 0 010-10.27zm0 1.802a3.333 3.333 0 100 6.666 3.333 3.333 0 000-6.666zm5.338-3.205a1.2 1.2 0 110 2.4 1.2 1.2 0 010-2.4z"
                    clip-rule="evenodd"
                  />
                </svg>
              </dt>
              <dd>
                <a 
                  class="hover:text-gray-900" 
                  href="https://www.instagram.com/codeg.a.c"
                  target="_blank"
                  rel="noopener noreferrer"
                >
                  @codeg.a.c
                </a>
              </dd>
            </div>
          </dl>
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
        <!-- Hidden input for Netlify Forms -->
        <input type="hidden" name="form-name" value="contact-codeg" />
        
        <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
          <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
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
                />
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
    const form = e.target
    const formData = new FormData(form)

    // Submit to Netlify
    const response = await fetch("/", {
      method: "POST",
      headers: { "Content-Type": "application/x-www-form-urlencoded" },
      body: new URLSearchParams(formData).toString()
    })

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }

    // Clear form after successful submission
    formData.value = {
      firstName: '',
      lastName: '',
      email: '',
      phone: '',
      message: ''
    }
    
    alert('Mensaje enviado con éxito. Nos pondremos en contacto contigo pronto.')
  } catch (error) {
    console.error('Error submitting form:', error)
    alert('Hubo un error al enviar el mensaje. Por favor, intenta de nuevo.')
  } finally {
    isSubmitting.value = false
  }
}
</script>