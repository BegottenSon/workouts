<script>
    import BrandCover from '../components/brand-guide/BrandCover.svelte'
    import BrandPage from '../components/brand-guide/BrandPage.svelte'

    let page = 1;
    function handleClick(ev) {
        if (page >= 2) {
            page = 1;
            ev.detail.page = page;
            
        }else{
            ++page;
            ev.detail.page = page;
        }
    }
</script>

{#if page === 1}
    <BrandCover on:pageTurn={handleClick}
    />

{:else if page === 2}
    <BrandPage on:pageTurn={handleClick}
    pageTitle = "Master Logo"
    pageNumber = "2"
    src = "https://res.cloudinary.com/begottenson/image/upload/c_scale,w_400/v1601428932/Begotten%20Sounds/Main_BSN_Logo.png"
    paraOne = "The Begotten Sounds master logo is set to be bold with a luxurious feel. 
    It has a thick font on Begotten Sounds that gives a strong presence and yet a clean look. 
    The  mix of this with the smaller tagline, 'Where Music Is Born', is meant to give a cinematic look."
    paraTwo = "The Icon is placed over top to finish  off the master logo. 
    It is to represent all around abstraction. 
    The icon is meant to give a strong and passionate feeling. 
    A symbol of  energy, creativity, and music."
    paraThree = "The Master logo will be used for big spaces, screens and applications that can display it in it's totality. 
    This should be used also at the end of all videos."
    />
{/if}



