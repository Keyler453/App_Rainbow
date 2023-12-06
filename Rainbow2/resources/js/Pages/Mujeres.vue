<template>
    <div>
      <Head title="Rainbow:" />
      <div class="background-image">
        <img src="/images/general.jpg" class=" max-w-full h-full object-cover " />
      </div>
      <div class="flex flex-col items-center">
        <div class="container">
          <div v-if="medicoData.length > 0" class="mt-8 flex flex-wrap -mx-2">
            <div
              v-for="medico in medicogral"
              :key="medico.id"
              class="card mx-4 mb-4"
              :class="'card-' + medico.id"
              @mouseover="changeTextColor(medico.id, true)"
              @mouseout="changeTextColor(medico.id, false)"
            >
              <div class="md:flex h-full">
                <div class="md:flex-shrink-0"></div>
                <div class="p-8 flex flex-col justify-between items-center w-full h-full">
                  <div class="flex flex-col mt-48">
                    <div class="uppercase tracking-wide text-sm text-white font-semibold text-center">
                      <h1>Tipo: {{ medico.userType }}</h1>
                    </div>
  
                    <h2 class="block mt-4 text-lg leading-tight font-medium text-white">
                      <h1>Nombre del consultorio: {{ medico.name }}</h1>
                    </h2>
                    <p class="mt-2 text-white"><h1>Correo: </h1>{{ medico.email }}</p>
                    <p class="mt-2 text-white"><h1>Cédula Profesional: </h1>{{ medico.professional_id }}</p>
                    <p class="mt-2 text-white"><h1>Nombre del doctor: </h1>{{ medico.name_doctor }}</p>
                    <p class="mt-2 text-white"><h1>Teléfono: </h1><a :href="'whatsapp://' + medico.phone">{{ medico.phone }}</a></p>
                    <p class="mt-2 text-white"><h1>Ubicación: </h1>{{ medico.ubicacion }}</p>
                  </div>
                </div>
              </div>
              <hr class="border-t-2 border-gray-300 my-6">
            </div>
          </div>
          <p v-else>No hay datos de médicos generales.</p>
        </div>
  
        <!-- Agrega el siguiente bloque para redirigir a la página de falda -->
        <Link :href="route('falda')" class="btn hover:bg-blue-500">
          Ir a la página de Falda
        </Link>
      </div>
  
      <!-- Sección Sobre Nosotros -->
      <section id="AboutUs" class="py-16 bg-white">
        <div class="container mx-auto text-center">
          <h2 class="text-4xl font-bold text-indigo-800 mb-4">Sobre Nosotros</h2>
          <p class="text-lg text-gray-700 mb-8">
            ¡Hola! Somos un grupo apasionado de estudiantes que actualmente cursamos la carrera de Ingeniería Informática. Nuestra misión es explorar y aprender de manera activa en el emocionante mundo de la tecnología.
          </p>
          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
            <div class="mb-8">
              <h3 class="text-xl font-semibold mb-2 text-indigo-800">Nuestra Visión</h3>
              <p class="text-gray-600">
                Buscamos aplicar nuestros conocimientos en informática para resolver desafíos significativos y contribuir al avance tecnológico.
              </p>
            </div>
            <div class="mb-8">
              <h3 class="text-xl font-semibold mb-2 text-indigo-800">Áreas de Enfoque</h3>
              <p class="text-gray-600">
                Nos especializamos en diversas áreas, como desarrollo de Aplicaciones Web, Seguridad Informatica y Administración de bases de datos.
              </p>
            </div>
            <div class="mb-8">
              <h3 class="text-xl font-semibold mb-2 text-indigo-800">Compromiso Académico</h3>
              <p class="text-gray-600">
                Mantenemos un compromiso constante con la excelencia académica y estamos siempre en busca de oportunidades para aprender y crecer.
              </p>
            </div>
          </div>
        </div>
      </section>
  
      <!-- Pie de Página -->
      <footer id="Contacto" class="bg-gray-900 text-white py-10">
        <div class="container mx-auto grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- Información de contacto -->
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4 text-indigo-500">Contacto</h3>
            <p class="text-gray-400">Dirección: Carret. Teapa-Tacotalpa Km 4.5 Ej. Fco Javier Mina, Teapa, Mexico, 86801 </p>
            <p class="text-gray-400">Teléfono: 932-000-00-00</p>
            <p class="text-gray-400">Correo Electrónico: difusion@regionsierra.tecnm.mx</p>
          </div>
  
          <!-- Enlaces a redes sociales, política de privacidad, términos y condiciones, etc. -->
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4 text-indigo-500">Enlaces</h3>
            <ul class="flex space-x-4">
              <li><a href="https://www.facebook.com/TecNMRSierra" class="text-gray-400 hover:text-white">Facebook</a></li>
              <li><a href="http://www.regionsierra.tecnm.mx/" class="text-gray-400 hover:text-white">Sitio Oficial</a></li>
              <li><a href="[Enlace a Política de Privacidad]" class="text-gray-400 hover:text-white">Política de Privacidad</a></li>
              <li><a href="[Enlace a Términos y Condiciones]" class="text-gray-400 hover:text-white">Términos y Condiciones</a></li>
            </ul>
          </div>
  
          <!-- Horario de atención -->
          <div class="mb-8">
            <h3 class="text-xl font-semibold mb-4 text-indigo-500">Horario de Atención</h3>
            <p class="text-gray-400">Lunes a Viernes: 9:00 am - 6:00 pm</p>
            <p class="text-gray-400">Sábado: 10:00 am - 2:00 pm</p>
            <p class="text-gray-400">Domingo: Cerrado</p>
          </div>
  
          <!-- Mapa de ubicación interactivo -->
          <div>
            <h3 class="text-xl font-semibold mb-4 text-indigo-500">Ubicación</h3>
            <div class="mb-4 aspect-w-1 aspect-h-1">
              <!-- Reemplaza las coordenadas con las reales para tu ubicación -->
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1646.693597231258!2d-92.91173068900828!3d17.54679147617257!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85c7eb8640ee430f%3A0x7a1b4f6d9f888c4c!2sTu%20Ubicaci%C3%B3n!5e0!3m2!1ses-419!2smx!4v1640177500002!5m2!1ses-419!2smx"
                width="100%"
                height="100%"
                style="border:0;"
                allowfullscreen=""
                loading="lazy"
              ></iframe>
            </div>
          </div>
        </div>
      </footer>
    </div>
  </template>
  
  
  <script setup>
  import { Head, Link } from '@inertiajs/vue3';
  import { defineProps } from 'vue';
  
  const props = defineProps(['medicogral']);
  
  if (!props.medicogral || props.medicogral.length === 0) {
    console.warn('No hay datos de médicos generales.');
  }
  
  const medicoData = props.medicogral;
  
  const changeTextColor = (medicoId, isHover) => {
    const cardTexts = document.querySelectorAll(`.card-${medicoId} .text-white, .card-${medicoId} .text-black`);
    const textColor = isHover ? 'black' : 'white';
    cardTexts.forEach((text) => {
      text.style.color = textColor;
    });
  
    // Almacenar el estado en localStorage
    localStorage.setItem(`card-${medicoId}`, textColor);
  };
  
  const restoreTextColors = () => {
    for (let i = 0; i < medicoData.length; i++) {
      const medicoId = medicoData[i].id;
      const storedColor = localStorage.getItem(`card-${medicoId}`);
      if (storedColor) {
        const cardTexts = document.querySelectorAll(`.card-${medicoId} .text-black, .card-${medicoId} .text-white`);
        cardTexts.forEach((text) => {
          text.style.color = storedColor;
        });
      }
    }
  };
  
  // Restaurar los colores al cargar la página
  restoreTextColors();
  </script>
  
  <style>
  .background-image {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    z-index: -1;
    overflow: hidden;
  }
  
  .background-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .card {
    flex: 0 0 calc(33.333% - 20px);
    width: 15cm;
    height: 17.5cm;
    margin: 10px;
    background: rgba(39, 37, 37, 0.486); /* Color de fondo */
    border-radius: 20px;
    overflow: hidden;
    box-sizing: border-box;
    position: relative;
    transition: transform 0.3s, box-shadow 0.3s;
  }
  
  .card:hover {
    transform: scale(1.05);
    box-shadow: 10px 10px 20px #c2c2c2, -10px -10px 20px #ffffff; /* Sombras para el efecto neumórfico */
  }
  
  .card:hover .text-black {
    color: black; /* Color del texto cuando se pasa el cursor */
  }
  
  .card:hover .text-white {
    color: white; /* Color del texto cuando se pasa el cursor */
  }
  
  .card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 20px;
    background: linear-gradient(45deg, #20b2d6, #ffffff); /* Degradado de fondo */
    z-index: -1;
    opacity: 0;
    transition: opacity 0.3s;
  }
  
  .card:hover::before {
    opacity: 1;
  }
  
  .card:not(:last-child) {
    margin-right: 10px;
  }
  </style>
  