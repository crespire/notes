# Testing

Testing and Test Driven Development are not the same thing, but often testing is introduced this way to make it a little easier to digest.

Testing is an important part of writing good code, as having a solid test suite is imparative when you are refactoring code. My experience with writing Chess in Ruby was very indicative of that. Had I not already built up my testing suite before I refactored the movement code, it would have been difficult to refactor without catching regressions or introducing new problems.

### Personal Testing Approach
I personally found that using mocks and doubles for code completely under my own control to be a frustrating and painful experience. Whether that had to do with my inexperience is yet to be seen (likely the case), but I found it much more straight forward to build my program and accompanying tests following an "inside->out" strategy (also known as _classic school_). That is, I started at the core of the program functionality I needed to enable the next "layer" of my program and continued to build out from there until my program was complete.

As a concrete example, in my Chess journey, I started with the Cell object for the Board, the moved to the Board, then moved to the Game object, etc, etc. Each new layer depended on the unit before, but in this way, I was able to avoid the use of mocks.

I think this strategy is great when building something from scratch.

I see value in the outside-in approach (aka _London school_) as well, but my inexperience with mocks is the primary barrier there, plus I haven't yet encountered a situation where outside-in made more sense to utilize. From a [Stride consulting article](https://www.stridenyc.com/blog/outside-in-vs-inside-out-tdd):

> Outside-in is also helpful when you aren’t sure where you’re going to get your data. It ends up being the last part of the process! This also means that we decouple the layers of the application, so you can swap out data sources easily and have confidence that the rest of the code will work as expected.
> I almost always advocate for outside-in testing when working on a story that has acceptance criteria. It focuses on how the data will be used, not on how it happened to be stored. I find that it guides my work more efficiently, since I know how I want the end result to be at the beginning. From the very first test to the last database call, every line of code I write is in service of that.

### Testing _Units_ vs Integration
Sandi Metz has a fantastic video from RailsConf about testing: https://www.youtube.com/watch?v=URSWYvyc42M

The bottom line is: focus on testing the unit's **interface**. Therefor, for any given unit, there are really only certain things you should focus on testing.
1. For any incoming message from another object, test that the unit responds in the expected way.
    * For an incoming query message, assert that the unit provides the correct result.
    * FOr an incoming command message, assert that the unit's public state is updated correctly.
1. For any outgoing messages, test that the unit sends the message, and that it sends the right message contents.

For all messages sent to self, or outgoing query messages, we don't really need to test them. Either these internal messages will be tested via the public interface, or in cases where there is a lot of internal, private logic, there may be a hidden abstraction that should be extracted. In cases where private logic is integral to the unit, there may be some benefit to exposing the methods/logic pubically for the purposes of testing (though I am not sure how to do this as a best practice in production/commercial code, stay tuned maybe I will find out!).

### Integration Testing
There is some value to testing integration (in what I've learned so far, these would be so called _system_ tests in a Rails context). My personal experience is currently limited to some Rails testing content, so I will leave this here for more future notes.
