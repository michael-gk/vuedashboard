<script setup>
import TeamMember from "@/components/TeamMember.vue";
import team from "../assets/team.json"

console.log(team)
</script>

<template>
  <header class="flex justify-between">
    <div>
      <button class="bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded disabled:bg-gray-400"
              :disabled="team.members.length === team.spots">Add Member ({{ team.spots - team.members.length }} Spots Left)
      </button>
    </div>
    <div>
      <div class="inline-flex items-center text-3xl relative">
        <img src="/smiley.png" alt="" class="mr-2">
        <h3>{{ team.name }} Team</h3>
        <div
            class="bg-green-400 w-5 h-5 text-xs text-white rounded-full flex justify-center items-center absolute -right-4 -top-2">
          {{ team.spots }}
        </div>
      </div>
    </div>
  </header>

  <div class="place-self-center flex flex-col gap-y-3">
    <table class="table-fixed border-spacing-2 border-separate">
      <thead>
      <th class="text-left px-6 py-2">Name</th>
      <th class="text-left px-6 py-2">Email</th>
      <th class="text-left px-6 py-2">Status</th>
      </thead>
      <tbody>
      <TeamMember v-for="member in team.members" :name="member.name" :email="member.email" :status="member.status"/>

      </tbody>
    </table>
    <p class="text-right text-gray-600 italic">There are no remaining team spots. Upgrade to add more.</p>
  </div>
  <footer class="mt-12 bg-gray-100 py-4 text-center">
    <h5 class="font-semibold text-lg">{{ team.name }} - {{ team.spots }} Member Team</h5>
  </footer>
</template>
