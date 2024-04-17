# audience-webplayer-sdk

`audience-webplayer-sdk` is a powerful, event-driven library designed to simplify the integration and management of `audience` video streaming capabilities within web applications. It allows developers to seamlessly connect to and control video streams, leveraging a modern API to manage playback, volume control, and state management.

# Quick Start

## Streamer
To start streaming using the `audience-webplayer-sdk`, follow these steps:

1. **Register an Account**
   - Visit our official website [meta-audience.com](http://www.meta-audience.com) and register an account.

2. **Access RTMP Settings**
   - Navigate to the RTMP settings page at [stream.meta-audience.com/:your-app-id](https://stream.meta-audience.com/:your-app-id). Replace `:your-app-id` with your actual application ID.

3. **Login**
   - Log in with your newly created account credentials.

4. **Create a Channel**
   - Once logged in, proceed to create a new channel where you will host your streams.

5. **Obtain Stream Credentials**
   - After creating your channel, copy the `Stream URL` and `Stream Key` from the channel settings. These will be used to configure your streaming software.

6. **Open OBS**
   - Launch Open Broadcaster Software (OBS) or any other streaming software you prefer.

7. **Setup Streaming**
   - In OBS, go to settings and set up your streaming configuration by entering the copied `Stream URL` and `Stream Key`. Ensure that your video and audio encoding settings are optimized for live streaming.

8. **Start Streaming**
   - After setting up your stream, go back to the main OBS screen and click the "Start Streaming" button. You should now be live!

Ensure your internet connection is stable throughout to maintain a high-quality stream.


## Viewer
### Installation
You can install audience-webplayer-sdk using npm:
```bash
npm install audience-webplayer-sdk
```
Or using yarn:
```bash
yarn add audience-webplayer-sdk
```

### Basic Usage

```ts
// Obtain a reference to your video element in the HTML
const videoElement = document.getElementById('myVideoPlayer');

// Create a new WebPlayer instance with the video element
const player = new WebPlayer({
    videoElement: videoElement
});

// Function to connect to a channel
async function connectToChannel(channelId) {
    try {
        const channel = await player.connect(channelId);
        console.log('Connected to channel:', channel.name);
    } catch (error) {
        console.error('Connection failed:', error);
    }
}

// You must first initialize the SDK by setting up your account configuration before connect to a channel.
initialize().then(channelTable => {
    const channelId = Object.values(channelTable)[0].id;  // Accessing the first channel ID
    connectToChannel(channelId).then(() => {
        console.log('Connection established successfully.');
    });
});

// Disconnecting from a Channel
document.getElementById('disconnectButton').addEventListener('click', () => {
    player.disconnect()
})
```

