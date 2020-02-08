<!-- Modal Component --> 
<template>
    <transition name="modal">
        <div class="
            modal-mask 
            flex 
            justify-center 
            items-center fixed z-50
            top-0 left-0
            w-full h-full"
        >
            <div class="modal-wrapper">
                <div class="
                    modal-container 
                    px-6 py-4
                    bg-white rounded-sm"
                >
                    <div class="modal-header">
                        <h3 class="
                            text-green-600
                            text-3xl
                            text-center py-3
                            font-semibold"
                        >
                            Saved! 👍 
                        </h3>
                    </div>


                    <div class="flex justify-center">
                        <button @click="$emit('close')" class="
                            bg-green-400 
                            shadow-lg text-sm
                            inline-block px-6 py-2 
                            bg-purple-800 text-white 
                            rounded-sm mt-3
                            font-bold tracking-wider" 
                        >
                            Close
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    name: 'Modal',
}
</script>

<style>
.modal-mask {
    background-color: rgba(0, 0, 0, .5);
    transition: opacity .3s ease;
}

.modal-container {
  width: 300px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
}

/* Transition styles */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(.9);
  transform: scale(.9);
}

</style>