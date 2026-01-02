<template>
    <v-container>
        <v-row>
            <v-col>
                <v-sheet class="pa-8" elevation="6">
                    <h1>Office Hours Calendar</h1>
                    <div style="margin-top: 2em;">
                        <vue-cal style="height: 1000px;" :events="events" :disable-views="['years', 'year']"
                            :time-cell-height="100" active-view="month" events-on-month-view=true />
                    </div>
                </v-sheet>
            </v-col>
        </v-row>
    </v-container>
</template>

<script lang="ts">
import VueCal from 'vue-cal'
import 'vue-cal/dist/vuecal.css'

import { defineComponent } from "vue";

function time_number_to_string(time: number) {
    if (time - Math.floor(time) < 0.5) {
        return String(Math.floor(time)) + ":00"
    } else {
        return String(Math.floor(time)) + ":30"
    }
}

var recesses = [
    {
        start: new Date("2024-10-15"),
        end: new Date("2024-10-21")
    },
    {
        start: new Date("2024-11-22"),
        end: new Date("2024-12-02")
    },
]

function getRecurringEventsStartEnd(start: string, end: string, day: number, name: string, loc: string, zoom_link: string, start_time: number, end_time: number) {
    var dates: { [key: string]: string }[] = []
    var start_date = new Date(start)
    var end_date = new Date(end)
    while (start_date < end_date) {
        start_date.setDate(start_date.getDate() + (((day + 7 - start_date.getDay()) % 7) || 7))
        var date = start_date.getFullYear() + '-' + String(start_date.getMonth() + 1).padStart(2, '0') + '-' + String(start_date.getDate()).padStart(2, '0')
        let in_recess = false
        for (let recess of recesses) {
            let date_object = new Date(date)
            if (date_object.getTime() >= recess.start.getTime() && date_object.getTime() < recess.end.getTime()) {
                in_recess = true
                break
            }
        }

        var contents: string[] = []
        if (loc) {
            contents.push(loc)
        }
        if (zoom_link) {
            contents.push(`<a href=${zoom_link}>zoom</a>`)
        }

        if (!in_recess) {
            dates.push({
                title: name,
                content: contents.join("<br>"),
                start: date + ' ' + time_number_to_string(start_time),
                end: date + ' ' + time_number_to_string(end_time),
            })
        }
    }
    return dates
}

function getRecurringEvents(day: number, name: string, loc: string, zoom_link: string, start_time: number, end_time: number) {
    return getRecurringEventsStartEnd("2024-09-02", "2024-12-01", day, name, loc, zoom_link, start_time, end_time)
}


// Weikang: Wednesday (time 12-1 pm, location, Dunham 432) 
// Tinglin: Friday Office Hour (time 1-2 pm, location: Dunham 432) 
// Chuhan: Monday Office Hour (time 9-10 am and location HLH 3rd floor)  
// Herlock: Thursdays Office Hour (Time 11:30-12:30 PM, location: Bass Library L34D) 
// Rishabh: Tuesday Office Hour (time 4-5pm, location: Tsai Center for Innovative Thinking 1st floor in front of reception desk) 
// David: Saturday Office Hour (time 1-2pm, location: Kline rm 211) 

function getWeikangEvents() {
    return getRecurringEvents(3, "Weikang", "Dunham 514", "", 12, 13)
}


function getTinglinEvents() {
    return getRecurringEvents(5, "Tinglin", "Dunham 432", "", 13, 14)
}

function getChuhanEvents() {
    return getRecurringEvents(1, "Chuhan", "HLH 3rd floor", "", 9, 10)
}

function getHerlockEvents() {
    return getRecurringEvents(4, "Herlock", "HLH17 Room 233", "", 14.5, 16)
}

function getRishabhEvents() {
    return getRecurringEvents(2, "Rishabh", "Tsai Center for Innovative Thinking 1st floor in front of reception desk", "", 16, 17)
}

function getDavidEvents() {
    return getRecurringEvents(6, "David", "Kline rm 211", "", 13, 14)
}


function getEvents() {
    return getWeikangEvents()
        .concat(getTinglinEvents())
        .concat(getChuhanEvents())
        .concat(getHerlockEvents())
        .concat(getRishabhEvents())
        .concat(getDavidEvents())
}


export default defineComponent({
    components: { VueCal },
    data: () => ({
        events: getEvents()
    })
})
</script>

<style>

.vuecal__event-title {
  font-size: 1.2em;
  font-weight: bold;
  /* margin: 4px 0 8px; */
}

.vuecal__event-time {
  display: inline-block;
  /* margin-bottom: 12px;
  padding-bottom: 12px; */
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
}

.vuecal__event-content {
  font-style: italic;
  font-size: 0.8em;
}
</style>
