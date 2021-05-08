# User Guide Driven Development

Start by writing out a User Guide, normally in markdown. It’s in plain english, describes how to use the software, showing all the examples by way of input and expected output.

Writing this document first, detailing from a user’s point of view what the functionality is and how to use it sets the direction of travel for the development phase.

Don’t think much about implementation at this point, consider the user experience. The implementation at this point is mostly like magic — pretend it will all be okay and just write the user guide of what will be.

This way we don’t have to worry about how technically hard a thing will be — just write out what we *want* it to do, as if writing user documentation for something that *already* exists.

Doing it in this order addresses the project from a human point of view, assuming the technology will catch up until they both meet somewhere.

It’s a very cheap way of discovering that this Great Idea maybe sucks a lot more than originally thought; just words on a page, no code written. 

I also somewhat heretically think that if the User Guide makes sense, then it’s just a case of turning the developer wheel until everything works.

So — the output of UGDD is the actual document the end user reads and follows to use the tool.

Then, after the UGDD is written out and evaluated as something approaching clear, sensible, usefult, I fall back to a flavour of TDD for the development.

## Testing the User Guide

In addition to regular unit, integration, component et cetera I have tests for the User Guide itself. I’m not sure what to call these tests so I stuck with User Guide Tests (UG).

The UG tests are regular unittest classes that call the application and assert that the input/output is **exactly**  as the User Guide says it will be. The important bit here is they don’t call the API of what I’m writing — they do STDIN/STDOUT validation of the end product.

This means the tests themselves look quite weird but it “proves” the overall experience. It also means when I inevitably change something, my UG tests fail for what might seem like an unimportant cosmetic issue but forces me to keep the docs and the code consistent.

As I write up new features, I start by extending the User Guide; this way, I read that back, conclude to myself that the approach is sensible, writeup some user guide tests which will then sit in a failing state until my implementation finally catches up via some TDD.

Wrapping up, UGDD encourages me to:

- stop thinking about code for a bit and more about the product
- proves the implementation is doing what the docs say
- (maybe) improve quality as a bunch of black-box tests

> Note: Silly/Shiny Idea For The Future: parse a user guide to create tests. Or a halfway house piece of documentation that contains markup from which a guide and test can be (easily, markdown-esque levels of complexity) produced.
