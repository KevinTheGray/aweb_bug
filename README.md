# aweb_bug
A project to demonstrate a bug with animated webps in flutter.

Animated webs with a specified n loops actually loop n+1 times.

## To reproduce
1. Clone this project
1. `flutter run` on any device or emulator 
1. Observe the top webp loops infinitely as expected (loop count of 0 specified), the second webp incorrectly loops twice (loop count of 1 specified), the third webp incorrectly loops three times (loop count of 2 specified).

You can validate thatthese files have the loop counts specified by either opening them in Chrome, or by inspecting the file with a hex editor and verify the loop chunks are set as stated.

Also, if you modify `image_stream.dart` and do this:
```
print(codec.repetitionCount);
print(codec.frameCount);
```
in the `_handleCodec` function, you can see the repetition count is set to -1 for 0-loop, 1 for 1-loop, and 2 for 2-loop.
