<script>
    import { Container, Row, Col, MaterialApp } from 'svelte-materialify';
    import GoogleNewsLab from '../../img/GoogleNewsLab.svelte'
    import ViT from '../../img/ViT.svelte'
    import UdG from '../../img/UdG.svelte'
    import Tweet from './Tweet.svelte'
</script>

<div class='fs footer'>
    <div class='col'>
    <Container>
        <h3>Like it? Share it!
            <Tweet
                tweet="Pandemics, wildfires, protests. What brought us together to offer ✨ help ✨ to those in need? We found some answers with Google's search index. Check it out! "
                url="https://mvtec-google-workshop-fuschia.vercel.app/"
            />
        </h3>
        <Row>
            <Col cols={12} sm={12} md={8}>
                
                
                <h4>The project</h4>
                <p><slot name='about'></slot></p>
                <h4>About the data</h4>
                <p><slot name='data'></slot></p>
            </Col>
            <Col cols={12} sm={12} md={4}>
                <h4>Made by</h4>
                <p><slot name='team'></slot></p>
                <p><b>Google News Lab:</b> <a href="https://twitter.com/beckypinners?lang=en" class="white-text">Becky Pinnington</a>, <a class="white-text" href='https://simonrogers.net/'>Simon Rogers</a> and <a class="white-text" href='http://albertocairo.com/'>Alberto Cairo</a></p>
                <p><b>MVTEC mentors: </b> <a class="white-text" href="https://www.karmapeiro.com/en/landing-en/">Karma Peiró</a> and <a class="white-text" href="https://www.linkedin.com/in/mosbrn/">Matt Osborn</a>.</p>
            </Col>
        </Row>
        <p>This project was designed and developed in the <a class="white-text" href='http://www.mastervisualtoolsudg.com/'>Master’s program in Visual Tools to Empower Citizens (MVTEC)</a> organized by <a class="white-text" href='https://www.fundacioudg.org/'>Fundació UdG</a> and the <a class="white-text" href='https://www.fundaciovit.org/'>ViT Foundation</a></p>
        <Row>
            <Col cols={12} sm={4}><GoogleNewsLab /></Col>
            <Col cols={12} sm={2}><ViT /></Col>
            <Col cols={12} sm={3}><UdG /></Col>
        </Row>
    </Container>
    </div>
</div>
	
<style>
    .footer {
        background-color:#284385;
        color:#FFF;
        padding-top:5rem;
    }
    .footer p {
        font-size: 1rem;
    }

    b {
        font-weight: 700;
    }

</style>