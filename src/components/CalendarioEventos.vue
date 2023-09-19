
<template>
    <div>
      <FullCalendar
        ref="calendar"
        :options="calendarOptions"
      />
  
      <button
        @click="addEvent"
        :disabled="!eventTitle || !eventDate || !eventTime"
        class="btn btn-primary"
      >
        Agregar evento
      </button>
  
      <input type="text" placeholder="Nombre del evento" v-model="eventTitle" />
      <input type="date" v-model="eventDate" />
      <input type="time" v-model="eventTime" />
    </div>
  </template>
  
  <script>
  import { Calendar } from "@fullcalendar/core";
  import dayGridPlugin from "@fullcalendar/daygrid";
  import timeGridPlugin from "@fullcalendar/timegrid";
  
  export default {
    name: "CalendarioEventos",
    data() {
      return {
        calendarOptions: {
          plugins: [dayGridPlugin, timeGridPlugin],
          defaultView: "dayGridMonth",
          events: [
            
          ],
        },
  
        eventTitle: "",
        eventDate: "",
        eventTime: "",  
      };
    },
    mounted() {
      this.calendar = new Calendar(this.$refs.calendar, this.calendarOptions);
      this.calendar.render();
    },
  
    methods: {
      addEvent() {
        // Verificar que el título del evento no sea vacío
        if (!this.eventTitle) {
          alert("Debes introducir un título para el evento");
          return;
        }

        if (!this.eventDate) {
            alert("Debes introducir una fecha para el evento");
            return;
        }

        if (!this.eventTime) {
            alert("Debes introducir una hora para el evento");
            return;
        }
  
        // Crear un objeto de evento
        const event = {
          title: this.eventTitle,
          start: `${this.eventDate}T${this.eventTime}`,
          
        };
  
        // Agregar el evento al calendario
        this.calendar.addEvent(event);
      },
    },
  };
  </script>
  







  
  