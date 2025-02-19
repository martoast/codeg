<template>
  <div class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <h2 class="text-4xl font-semibold tracking-tight text-balance text-gray-900 sm:text-5xl">Eventos</h2>
        <p class="mt-2 text-lg/8 text-gray-600">Sé parte del cambio: Únete a nuestros eventos transformadores</p>
      </div>
      <div class="mx-auto mt-16 grid max-w-2xl auto-rows-fr grid-cols-1 gap-8 sm:mt-20 lg:mx-0 lg:max-w-none lg:grid-cols-3">
        <article v-for="event in events" :key="event.id" class="relative isolate flex flex-col justify-end overflow-hidden rounded-2xl bg-gray-900 px-8 pt-80 pb-8 sm:pt-48 lg:pt-80">
          <img :src="event.imageUrl" alt="" class="absolute inset-0 -z-10 size-full object-cover" />
          <div class="absolute inset-0 -z-10 bg-gradient-to-t from-gray-900 via-gray-900/40" />
          <div class="absolute inset-0 -z-10 rounded-2xl ring-1 ring-gray-900/10 ring-inset" />
          
          <div class="flex flex-wrap items-center gap-y-1 overflow-hidden text-sm/6 text-gray-300">
            <time :datetime="event.datetime" class="mr-8">{{ event.date }}</time>
            <div class="-ml-4 flex items-center gap-x-4">
              <svg viewBox="0 0 2 2" class="-ml-0.5 size-0.5 flex-none fill-white/50">
                <circle cx="1" cy="1" r="1" />
              </svg>
              <div class="flex gap-x-2.5">
                <span class="px-2 py-1 text-xs font-medium rounded-full" 
                      :class="event.isUpcoming ? 'bg-green-500/10 text-green-400' : 'bg-gray-500/10 text-gray-300'">
                  {{ event.isUpcoming ? 'Próximo Evento' : 'Evento Pasado' }}
                </span>
              </div>
            </div>
          </div>
          
          <h3 class="mt-3 text-lg/6 font-semibold text-white">
            <a :href="event.href">
              <span class="absolute inset-0" />
              {{ event.title }}
            </a>
          </h3>
          
          <p class="mt-2 text-sm text-gray-300">{{ event.location }}</p>
          
          <div v-if="event.isUpcoming" class="mt-4">
            <a :href="event.registrationLink" 
               class="inline-block px-4 py-2 text-sm font-semibold text-white bg-indigo-600 rounded-lg hover:bg-indigo-500 transition-colors">
              Registrarme
            </a>
          </div>
        </article>
      </div>
    </div>
  </div>
</template>

<script setup>
const events = [
  {
    id: 1,
    title: 'Taller de Liderazgo Juvenil',
    href: '#',
    location: 'CETYS Universidad, Campus Mexicali',
    imageUrl: '/1.jpeg',
    date: '24 de Marzo, 2024',
    datetime: '2024-03-24',
    isUpcoming: true,
    registrationLink: '#'
  },
  {
    id: 2,
    title: 'Conferencia: Valores Familiares en la Era Digital',
    href: '#',
    location: 'Tecnológico de Monterrey, Campus Mexicali',
    imageUrl: '/2.jpeg',
    date: '15 de Abril, 2024',
    datetime: '2024-04-15',
    isUpcoming: true,
    registrationLink: '#'
  },
  {
    id: 3,
    title: 'Encuentro de Jóvenes Líderes',
    href: '#',
    location: 'Centro Cultural de Mexicali',
    imageUrl: '/3.jpeg',
    date: '10 de Febrero, 2024',
    datetime: '2024-02-10',
    isUpcoming: false
  }
]
</script>