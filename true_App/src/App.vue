<script setup>
import { ref } from "vue";
const opportunityOpen = ref(false);
const feedbackOpen = ref(false);
const menuOpen = ref(false);
const language = ref("th");

const toggleLanguage = () => {
  language.value = language.value === "th" ? "en" : "th";
};

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};
const toggleOpportunity = () => {
  opportunityOpen.value = !opportunityOpen.value;
};
const toggleFeedback = () => {
  feedbackOpen.value = !feedbackOpen.value;
};
</script>
<template>
  <div class="min-h-screen bg-gray-50 flex flex-col">
    <!-- Navbar -->
    <header
      class="flex items-center justify-between px-4 py-3 shadow-md bg-white"
    >
      <!-- Hamburger -->
      <button @click="toggleMenu">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-6 w-6 text-gray-700"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
      </button>

      <!-- Logo -->
      <h1 class="text-xl font-bold">
        <span class="text-red-600">CRM</span
        ><span class="text-pink-500">Lite</span>
      </h1>

      <!-- Home icon (placeholder) -->
      <button>
        <span class="w-6 h-6 block bg-gray-300 rounded"></span>
      </button>
    </header>

    <!-- Sidebar Overlay -->
    <div
      v-show="menuOpen"
      @click="toggleMenu"
      class="fixed inset-0 bg-opacity-50 transition-opacity duration-300 z-40"
    ></div>

    <!-- Sidebar Menu -->
    <aside
      class="fixed top-0 left-0 h-full w-72 bg-white shadow-lg transform transition-transform duration-300 z-50"
      :class="menuOpen ? 'translate-x-0' : '-translate-x-full'"
    >
      <!-- Header -->
      <div class="p-4 border-b">
        <h2 class="text-lg font-semibold">Nawarat Timdang</h2>
        <p class="text-sm text-gray-600">90009632</p>
        <p class="text-sm text-gray-600">TEAM_USER TS80000784</p>
        <span
          class="inline-block mt-2 px-2 py-0.5 text-xs bg-gray-200 text-gray-700 rounded"
          >PDS</span
        >
      </div>

      <!-- Menu List -->
      <nav class="mt-2">
        <ul class="flex flex-col text-gray-700">
          <li>
            <button
              class="flex items-center w-full px-4 py-3 hover:bg-gray-100"
            >
              <span class="mr-3 w-5 h-5"></span> My Task
            </button>
          </li>
          <li>
            <button
              class="flex items-center justify-between w-full px-4 py-3 hover:bg-gray-100"
              @click="toggleOpportunity"
            >
              <span class="flex items-center">
                <span class="mr-3 w-5 h-5"></span> Opportunity
              </span>
              <svg
                class="w-4 h-4 transform transition-transform duration-300"
                :class="opportunityOpen ? 'rotate-180' : ''"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M19 9l-7 7-7-7"
                />
              </svg>
            </button>
            <ul v-show="opportunityOpen" class="ml-10 text-sm text-gray-600">
              <li class="py-1">Sub Menu 1</li>
              <li class="py-1">Sub Menu 2</li>
            </ul>
          </li>

          <!-- Feedback -->
          <li>
            <button
              class="flex items-center justify-between w-full px-4 py-3 hover:bg-gray-100"
              @click="toggleFeedback"
            >
              <span class="flex items-center">
                <span class="mr-3 w-5 h-5"></span> Feedback
              </span>
              <svg
                class="w-4 h-4 transform transition-transform duration-300"
                :class="feedbackOpen ? 'rotate-180' : ''"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M19 9l-7 7-7-7"
                />
              </svg>
            </button>
            <ul v-show="feedbackOpen" class="ml-10 text-sm text-gray-600">
              <li class="py-1">Sub Menu A</li>
              <li class="py-1">Sub Menu B</li>
            </ul>
          </li>
          <li>
            <button
              class="flex items-center w-full px-4 py-3 hover:bg-gray-100"
            >
              <span class="mr-3 w-5 h-5"></span> Prepaid Register
            </button>
          </li>
          <li>
            <button
              class="flex items-center w-full px-4 py-3 hover:bg-gray-100"
            >
              <span class="mr-3 w-5 h-5"></span> Campaign
            </button>
          </li>
          <li>
            <button
              class="flex items-center w-full px-4 py-3 hover:bg-gray-100"
            >
              <span class="mr-3 w-5 h-5"></span> Check Owner & Eligible
            </button>
          </li>
          <li>
            <button
              class="flex items-center w-full px-4 py-3 hover:bg-gray-100"
            >
              <span class="mr-3 w-5 h-5"></span> Sign out
            </button>
          </li>
          <li
            class="flex items-center justify-between px-4 py-3 hover:bg-gray-100"
          >
            <span class="flex items-center">
              <span class="mr-3 w-5 h-5"></span> Language
            </span>

            <!-- Toggle -->
            <button
              @click="toggleLanguage"
              class="relative flex items-center h-7 w-16 rounded-full transition-colors duration-300"
              :class="language === 'th' ? 'bg-blue-500' : 'bg-green-500'"
            >
              <!-- Ball -->
              <span
                class="absolute top-1 left-1 w-5 h-5 bg-white rounded-full shadow transform transition-transform duration-300"
                :class="language === 'th' ? 'translate-x-0' : 'translate-x-9'"
              ></span>

              <!-- Text -->
              <span
                class="absolute inset-0 flex items-center justify-center text-xs font-semibold text-white transition-all duration-300"
              >
                <span v-if="language === 'th'" class="ml-6">TH</span>
                <span v-else class="mr-6">EN</span>
              </span>
            </button>
          </li>
        </ul>
      </nav>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 flex justify-center items-start px-4 py-6">
      <div
        class="w-full max-w-md bg-white rounded-lg shadow-md overflow-hidden"
      >
        <!-- Header -->
        <div
          class="bg-pink-500 text-white text-center py-3 font-medium text-base"
        >
          ค้นหา
        </div>

        <!-- Body -->
        <div class="p-4">
          <p class="text-gray-700 mb-4 text-sm leading-relaxed">
            กรุณาระบุชื่อ, หมายเลขบัตรประชาชน, หมายเลขพาสปอร์ต หรือ
            หมายเลขบริการ
          </p>
          <div class="flex items-center border rounded-md overflow-hidden">
            <input
              type="text"
              placeholder="ค้นหา..."
              class="flex-1 px-3 py-2 outline-none text-gray-700 text-sm"
            />
            <button class="px-3 text-gray-500">
              <span class="w-5 h-5 block"></span>
            </button>
          </div>
        </div>

        <!-- Footer Buttons -->
        <div
          class="flex flex-col sm:flex-row justify-center gap-3 p-4 border-t"
        >
          <button
            class="bg-pink-500 text-white px-6 py-2 rounded-md shadow-md hover:bg-pink-600 text-sm"
          >
            ค้นหา
          </button>
          <button
            class="bg-gray-200 text-gray-700 px-6 py-2 rounded-md shadow-md hover:bg-gray-300 text-sm"
          >
            อ่านบัตร
          </button>
        </div>
      </div>
    </main>
  </div>
</template>
