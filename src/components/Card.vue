<!-- Card Component --> 
<template>
    <div class="max-w-md mx-auto">
        <div class="bg-white rounded-sm p-4 shadow-lg">
            <!-- Progress Bar --> 
            <div class="loading-bar pt-4 mt-2">
                <div class="currentGoal" 
                    :style="{'width': percentage() + '%'}">
                </div>
            </div>
            <!-- Main Section -->
            <h1 class="
                inline-block 
                my-4 font-bold
                text-2xl"
            >
                ${{raised}} 
                <span class="
                text-sm 
                text-gray-500 
                font-semibold"
                >
                    raised of ${{goal}} goal
                </span> 
            </h1>

            <p class="text-lg pb-4 text-gray-600">
                <span class="text-red-600 font-semibold">
                    Only 3 days left
                </span>
                to fund this project.
            </p>

            <p class="text-gray-600">
                Join the 42 other donors who have already 
                supported this project. 
                Every dollor helps.
            </p>

            <!-- Donate Section --> 
            <div class="mt-6 flex flex-wrap justify-between">
                <div class="
                    shadow-lg 
                    border 
                    flex 
                    items-center"
                >
                    <span class="
                        px-2
                        text-xl 
                        font-bold">
                        $
                    </span>
                    <input v-model="donate" type="number" 
                        class="
                        w-full
                        appearance-none
                        font-bold
                        text-xl
                        h-full
                        px-1"
                    />
                </div>

                <div class="shadow-lg text-lg">
                    <button @click="add"
                    href="#" class="
                    px-3 py-3
                    bg-purple-800 text-white 
                    rounded-sm
                    font-bold tracking-wider">
                    Give Now
                    </button>
                </div>
            </div>
            <span class="
            text-sm
            text-green-500
            inline-block 
            mt-3
            pl-2">
                <i>
                    Why give $50?
                </i>
            </span>
        </div>

        <!-- Footer Buttons -->
        <div class="flex justify-around mt-4">
                <a @click="showModal = true"
                    href="#" class="
                    shadow-lg text-lg
                    inline-block px-5 py-3 
                    text-purple-900 border-2
                    rounded-sm border-purple-900
                    font-bold tracking-wider">
                    Save for later
                </a>
                <a href="#" class="
                    shadow-lg text-lg
                    inline-block px-5 py-3 
                    text-purple-900 border-2
                    rounded-sm border-purple-900
                    font-bold tracking-wider">
                    Tell your friends
                </a>
        </div>
        <!-- Hidden Modal (Dialog box) -->
        <modal 
            v-if="showModal" 
            @close="showModal = false">
        </modal>
    </div>
</template>

<script>

import Modal from './Modal'


export default {
    name: 'Card',
    data: () => {
        return {
            goal: 1000,
            raised: 250,
            // Dynamic value linked to input tag
            donate: 0,
            showModal: false,
        }
    },
    methods: {
        // Called when the "Give Now" Button is clicked
        add: function() {
            this.raised += Number(this.donate);
            this.donate = 0
        },

        // Convert the money donated into %
        percentage: function() {
            let total = Math.floor((this.raised / this.goal) * 100)
            return total 
        }
    },
    components: {
        Modal,
    }
}
</script>

<style lang="scss" scoped>

/* Progress bar styles */
.loading-bar {
  position: relative;
  width: 100%;
  height: .4rem;
  border-radius: 15px;
  overflow: hidden;
  border-bottom: 1px solid #ddd;
  background-color: rgba(204, 241, 224, 0.7);

  .currentGoal {
    position: absolute;
    top: 1px; left: 1px; right: 1px;
    display: block;
    height: 100%;
    border-radius: 15px;
    background-color: #00b964;
    background-size: 30px 30px;
    transition: all 0.3s;
  } 
}

</style>