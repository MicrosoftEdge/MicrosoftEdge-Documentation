# Cortana voice commands

You can take advantage of Cortana integration by specifying a Voice Command Definition (VCD) file in your html page. The VCD file is an xml file that maps commands to specific phrases. For example, a user could tap the Start button and say “Contoso Books, show best sellers” to both launch the Contoso Books app and to navigate to a “best sellers” page.

When you add a `<meta>` element tag that lists the location of your VCD file, Windows automatically downloads and registers the Voice Command Definition file.

## Snippet

Here is an example of the use of the tag in an html page in a hosted web app:

```HTML
<meta name="msapplication-cortanavcd" content="https://contoso.com/vcd.xml"/>
```

## Related topics
[Cortana Dev Center](https://developer.microsoft.com/en-us/cortana)

[Cortana interactions and Voice Command Definition (VCD) elements and attributes v1.2](https://docs.microsoft.com/en-us/uwp/schemas/voicecommands/voice-command-elements-and-attributes-1-2)

[Cortana voice command](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CortanaVoiceCommand) sample

[Speech interactions](https://docs.microsoft.com/en-us/windows/uwp/design/input/speech-interactions)