<script>
    let title = 'A&A  Grocery List'
</script>

<div class="heading">
    <span class="title">{title}</span>
    <a href="https://flipp.com/flyers" target="_blank">flipp</a>
</div>


<div class="settings">
    <img src="fruits.png" alt="vegies" class="header-image"/>
</div>

<style>
    .title {
        color: aliceblue;
        font-size: x-large;
        font-family: 'Original Surfer', cursive;
    }
    .heading {
        text-align: center;
        background-color:brown;
        margin-top: 0;
        padding: 20px;
		font-size: 1em;
        font-weight:bold;
        font-family: 'Original Surfer', cursive;
	}

    .heading a {
        float: right;
        margin-right: 20px;
        padding-right: 10x;
        color:chartreuse;
        text-decoration: none;
        font-size: x-large;   
    }

    a:hover {
        color:aliceblue;
    }

    img {
        display: block;
        width: 100%;
        height: 200px;
        margin-right: auto;
        object-fit: cover;
}

@media(max-width:480px) {
    .heading {
        text-align: center;
        font-weight: 100;
        padding: 28px;
    }

    .title {
        font-size: medium;
    }
    .heading a {
        margin-right: 0;
        padding-right: 9px;
        font-size:smaller;
    }
}
</style>

<!-- markup (zero or more items) goes here -->