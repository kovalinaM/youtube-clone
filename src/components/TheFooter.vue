<template>
       <div>
        <a v-for="link in links.slice(0,7)" :key="link" href="#" class="mr-2">{{ link }}</a>
        <!-- <a href="#" class="mr-2">About</a>
        <a href="#" class="mr-2">Press</a>
        <a href="#" class="mr-2">Copyright</a>
        <a href="#" class="mr-2">Contact us</a>
        <a href="#" class="mr-2">Creators</a>
        <a href="#" class="mr-2">Advertise</a>
        <a href="#" class="mr-2">Developers</a> -->
      </div>
      <div>
        <a v-for="link in links.slice(8,11)" :key="link" href="#" class="mr-2">{{ link }}</a>
        <!-- <a href="#" class="mr-2">Terms</a>
        <a href="#" class="mr-2">Privacy</a>
        <a href="#" class="mr-2">Policy & Safety</a>
        <a href="#" class="mr-2">How YouTube works</a>
        <a href="#" class="mr-2">Test new features</a> -->
      </div>
      <div class="font-normal text-gray-500">
        &copy; 2021 Google LLC
      </div>
</template>

<script>
export default {
    data() {
        return {
            links: [
            'About',
            'Press',
            'Copyright',
            'Contact us',
            'Creators',
            'Advertise',
            'Developers',
            'Terms',
            'Privacy',
            'Policy & Safety',
            'How YouTube works',
            'Test new features'
            ]
        }
    }
}
</script>