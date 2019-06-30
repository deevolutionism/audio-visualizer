## Audio Visualizer
A minimalistic audio visualizer


#### Description:

Web Audio experiment for audio visualization on canvas.

![visualizer](/screenshots/visualizer.png "visualizer")


#### Usage

Include visualizer script in your index.html

````html
    <script src="visualizer.js"></script>
````

Include `audio` and `canvas` HTML elements with a click event to initialize the visualizer. the click event is neccessary to play audio - otherwise chrome or firefox will block it.
````html
    <div>
        <audio id="myAudio" src="path/to/source/audio/" data-author="insert/author/name" data-title="insert/audio/name"></audio>
        <canvas onclick="initVisualizer()" id="myCanvas" width="800" height="800"></canvas>
    </div>
````

include script for handling the initilization event
````js
let AV;
        
function initVisualizer() {
    if(!AV) {
        AV = AUDIO.VISUALIZER.getInstance({
            autoplay: false,
            loop: true,
            audio: 'myAudio',
            canvas: 'myCanvas',
            style: 'lounge',
            barWidth: 2,
            barHeight: 2,
            barSpacing: 7,
            barColor: '#cafdff',
            shadowBlur: 20,
            shadowColor: '#ffffff',
            font: ['12px', 'Helvetica']
        });
    }
}
````

**Note**: For visualizer to render audio and author names you'll have to set `data-author` and `data-title` attributes on your audio element.


Create Visualizer instance.

````js
    AUDIO.VISUALIZER.getInstance({
        audio: 'myAudio',
        canvas: 'myCanvas',
    });
````

#### Options

| option | type | required | default | description |
| ------ | ---- | -------- | ------- | ----------- |
| audio  | string | True | 'audio-sample-1' | html audio element ID |
| canvas | string | True | 'canvas-1' | html canvas element ID |
| autoplay | string | Boolean | False | auto start visualizer (functionality varies depending on browser policy) |
| loop | Boolean | false | false | toggle looping |
| style | String | false | 'lounge' | pick the visualizer type. currently only one type named 'lounge' | 
| radius | Interger | false | canvas width / 2 | sets radius of the visualizer |
| circumferenceSlice | Float | false | 0.0 | determines what chunk of the bars you want to be removed. 0 to show all 1 to show none. |
| barWidth | Integer | false | 2 | sets width of bars |
| barHeight| Integer | false | 2 | sets height of bars |
| barSpacing | Integer | false | 5 | sets spacing between bars |
| barColor | String | false | '#fff' | sets color of bars |
| shadowBlur | String | false | 10 | sets shadow blur of bars |
| shadowColor | String | false | '#fff' | sets shadow color of bars |
| font | Array | false | ['12px', 'helvetica'] | sets font of text | 


#### CSS Styles
Style by your own preference or you can use these defaults.

````html
<div class="vz-wrapper">
    <audio id="myAudio" src="path/to/source/audio" data-author="insert/author/name" data-title="insert/audio/name"></audio>

    <div class="vz-wrapper -canvas">
        <canvas id="myCanvas" width="800" height="400"></canvas>
    </div>
</div>
````

````css
body {
    margin: 0;
}

.vz-wrapper {
    position: relative;
    height: 100vh;
    width: 100%;
    background: -webkit-gradient(radial, center center, 0, center center, 460, from(#396362), to(#000000));
    background: -webkit-radial-gradient(circle, #396362, #000000);
    background: -moz-radial-gradient(circle, #396362, #000000);
    background: -ms-radial-gradient(circle, #396362, #000000);
    box-shadow: inset 0 0 160px 0 #000;
    cursor: pointer;
}

.vz-wrapper.-canvas {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: initial;
    width: initial;
    background: transparent;
    box-shadow: none;
}

@media screen and (min-width: 420px) {
    .vz-wrapper {
        box-shadow: inset 0 0 200px 60px #000;
    }
}
````

[Live preview](http://davidlazic.github.io/audio-visualizer)
