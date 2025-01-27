# API Docs - v2.0.1

!!! Info "Tested Siddhi Core version: *<a target="_blank" href="http://siddhi.io/en/v5.0/docs/query-guide/">5.0.0</a>*"
    It could also support other Siddhi Core minor versions.

## Sink

### googlepubsub *<a target="_blank" href="http://siddhi.io/en/v5.0/docs/query-guide/#sink">(Sink)</a>*
<p style="word-wrap: break-word">The GooglePubSub sink publishes messages to a topic in the GooglePubSub server. If the required topic does not exist, GooglePubSub Sink creates the topic and publishes messages to it.</p>
<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>

```
@sink(type="googlepubsub", project.id="<STRING>", topic.id="<STRING>", credential.path="<STRING>", @map(...)))
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">project.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The unique ID of the GCP console project within which the topic is created.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">topic.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The ID of the topic to which the messages that are processed by Siddhi are published. </td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">credential.path</td>
        <td style="vertical-align: top; word-wrap: break-word">The file path of the service account credentials.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
@sink(type = 'googlepubsub', @map(type= 'text'),
project.id = 'sp-path-1547649404768', 
credential.path = 'src/test/resources/security/sp.json',
topic.id ='topicA',
 )
define stream InputStream(message string);
```
<p style="word-wrap: break-word">This query publishes messages to a topic in the GooglePubSub server. Here, the messages are published to'topicA' topic in the 'sp-path-1547649404768' project. If the 'topicA' topic already exists in the 'sp-path-1547649404768' project, messages are directly published to that topic. If it does not exist, a topic with that ID is newly created in the project and then, the messages are published to that topic.</p>

## Source

### googlepubsub *<a target="_blank" href="http://siddhi.io/en/v5.0/docs/query-guide/#source">(Source)</a>*
<p style="word-wrap: break-word">The GooglePubSub source receives events to be processed by Siddhi from a topic in a GooglePubSub server. Here, a subscriber client creates a subscription to that topic and consumes messages via the subscription. The subscription applications receive only the messages that are published after the subscription is created. A subscription connects a topic to a subscriber application, enabling the application to receive and process messages from that topic. A topic can have multiple subscriptions, but a given subscription belongs only to a single topic.</p>
<span id="syntax" class="md-typeset" style="display: block; font-weight: bold;">Syntax</span>

```
@source(type="googlepubsub", project.id="<STRING>", topic.id="<STRING>", subscription.id="<STRING>", credential.path="<STRING>", @map(...)))
```

<span id="query-parameters" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">QUERY PARAMETERS</span>
<table>
    <tr>
        <th>Name</th>
        <th style="min-width: 20em">Description</th>
        <th>Default Value</th>
        <th>Possible Data Types</th>
        <th>Optional</th>
        <th>Dynamic</th>
    </tr>
    <tr>
        <td style="vertical-align: top">project.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The unique ID of the GCP console project within which the topic is created.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">topic.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The unique ID of the topic from which the messages are received.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">subscription.id</td>
        <td style="vertical-align: top; word-wrap: break-word">The unique ID of the subscription from which messages must be retrieved.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
    <tr>
        <td style="vertical-align: top">credential.path</td>
        <td style="vertical-align: top; word-wrap: break-word">The file path of the service account credentials.</td>
        <td style="vertical-align: top"></td>
        <td style="vertical-align: top">STRING</td>
        <td style="vertical-align: top">No</td>
        <td style="vertical-align: top">No</td>
    </tr>
</table>

<span id="examples" class="md-typeset" style="display: block; font-weight: bold;">Examples</span>
<span id="example-1" class="md-typeset" style="display: block; color: rgba(0, 0, 0, 0.54); font-size: 12.8px; font-weight: bold;">EXAMPLE 1</span>
```
@source(type='googlepubsub',@map(type='text'),
topic.id='topicA',
project.id='sp-path-1547649404768',
credential.path = 'src/test/resources/security/sp.json',
subscription.id='subA',
)
define stream OutputStream(message String);
```
<p style="word-wrap: break-word">This query shows how to subscribe to a googlepubsub topic. Here, a googlepubsub source subscribes to the 'topicA' topic that resides in the 'sp-path-1547649404768' project within a googlepubsub instance. The events are received in the text format, mapped to a Siddhi event, and then sent to a stream named OutputStream.</p>

