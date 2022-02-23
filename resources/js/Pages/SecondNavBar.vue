<template>

        <div class="flex flex-row gap-12 pl-12 w-screen py-5 bg-gray-100/80 min-h-[50px] text-[0.9em] font-bold" id="navbar">
            <div>
            <span>
                About
            </span>
            </div>
            <div>
            <span>
                Jobs
            </span>
            </div>
            <div>
            <span>
                Apprenticeship
            </span>
            </div>
        </div>

</template>

<script>
export default {
    name: "SecondNavBar",
    setup() {
        window.onscroll = function() {scrollFunction()};

        function scrollFunction() {
            const navbar = document.getElementById('navbar');
            const sticky = navbar.offsetTop;
            navbar.style.zIndex = '3';
            if (window.pageYOffset > sticky) {
                navbar.classList.add('sticky');
            } else {
                navbar.classList.remove('sticky');
            }

            //if (window.pageYOffset > sticky )

            /*if (document.documentElement.scrollTop > 150 ) {
                navbar.style.position='relative';
            }
            if (document.documentElement.scrollTop > 60 && document.documentElement.scrollTop < 150) {
                navbar.style.top='0';
                navbar.style.position='fixed';

            } else {
                    navbar.style.position="relative";
            }
            */

        }
    }
}
</script>

<style scoped>
.sticky {
    animation-duration: 3s;
    top: 0;
    z-index: 1;
    position: fixed;
    transition-timing-function: ease-in-ease-out;
}
</style>
