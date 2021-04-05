

Media PeerPool is a CDN agnostic system that reduces up to 99% of bandwidth costs for media platforms by leveraging peer-to-peer browser functionality. It works as a peer-assisted solution in which all downloaders of a specific file, or viewers of the same stream share content with each other via WebRTC (allows data sharing to work inside web pages by allowing direct peer-to-peer communication) based on location and latency, reducing the load of the network dramatically, thus improving the overall performance.

### Live Streaming Example

Since PeerPool uses only Javascript, the integration is seamless to the end-user and only requires a small change in your site's HTML page.

### Client-Side Integration

Client-side integration depends on the player you are using and usually means adding one line of code to your page.
Add the following scripts to the head of your player's page:

```html
<script src="https://media.network/demo/peerpool.js"></script>
```

### Complete Example (Clappr)

```html

<style>body{margin:0}#video{width:100vw;height:100vh;}</style>
<div id="video"></div>
<script src="https://media.network/demo/peerpool.js"></script>
<script src="https://cdn.jsdelivr.net/npm/clappr@latest"></script>
<script>
  if (p2pml.hlsjs.Engine.isSupported()) {
    var engine = new p2pml.hlsjs.Engine();
    var loader = engine.createLoaderClass();
  } else {
    var loader = XHRLoader;
  }
  var engine = new p2pml.hlsjs.Engine();
  var player = new Clappr.Player({
    parentId: "#video",
    source: "https://etatlmcmsoieekfnrhkj2kyy3moabhu6nqvpsfij5tds.medianet.work/live/STREAM_NAME/index.m3u8",
    width:"100%",
    height:"100%",
    playback: {
      hlsjsConfig: {
        liveSyncDurationCount: 7,
        loader: loader
      }
    }
  });
  if (p2pml.hlsjs.Engine.isSupported()) p2pml.hlsjs.initClapprPlayer(player);
  player.play(true);
</script>

```
