---
layout: post
---

An article with various blocks of highlighted code snippets.

```ruby
=begin
  Dummy class nested inside a dummy module
  Private API
=end
```
```diff
- This line is redacted
- This line has been deleted
+ This line is visible
+ This line has been inserted
This line has not been changed
```
```sass
@import "base"

.card
  display: inline-block
  margin: 0
  padding: 0

  &:hover
    color: #ab45ef;
```
```ruby
21 + 54 = 0
foo ||= bar
foo / bar

24
45.75
0x2C716
\x0A
01010

/ya?ml/
"yaml"
```
```ruby
include Enumerable

module Foo
  class Bar
    LIPSUM = "lorem ipsum dolor sit"

    attr_reader :layout

    def initialize
      @layout = Layout.new
    end

    # instance method
    def profile
      measure_time do
        compile layout
        layout.render_with Bar::LIPSUM
      end
    rescue ArgumentError
      false
    end
  end
end

# Execute code
Foo::Bar.new.profile
```

{% raw %}
```liquid
{% assign foo = page.foo | bar: 'baz' %}
{{ foo }}
```
{% endraw %}

```yaml
author:
  admin: true
  name: John Doe
  email: johndoe@example.com
  id: 75636474
```

{% highlight html %}
<html>
  <head>
    <meta charset="utf-8" />
    <title>Hello World</title>
  </head>
  <body>
    <p>Hello, World!</p>
  </body>
</html>
{% endhighlight %}

{% highlight html mark_lines="1 4 7" %}
<html>
  <head>
    <meta charset="utf-8" />
    <title>Hello World</title>
  </head>
  <body>
    <p>Hello, World!</p>
  </body>
</html>
{% endhighlight %}

{% highlight html linenos %}
<html>
  <head>
    <meta charset="utf-8" />
    <title>Hello World</title>
  </head>
  <body>
    <p>Hello, World!</p>
  </body>
</html>
{% endhighlight %}

{% highlight html linenos mark_lines="1 4 7" %}
<html>
  <head>
    <meta charset="utf-8" />
    <title>Hello World</title>
  </head>
  <body>
    <p>Hello, World!</p>
    ✓ Learn Spanish
✓ Live in another country
✓ Start a nonprofit organization
✗ See my book being sold at an airport outside Vietnam
✓ Be in a movie/commercial (I’ve actually done this in 3 countries: Vietnam, India, US)
✗ Become the first author of a paper at a top-tier conference
✗ Get published on the New Yorker
✗ Read 1000 books (~60% done)
✓ Teach a graduate-level course
✓ Start a company
✗ Author a patent
✗ Write for a TV show that I watch
✗ Design and publish a game
✓ Fall in love
✓ Build a home (a simple one, but it’s mine)
✗ Have a salad from my garden
✗ Become a parent
✗ Be a writer in Paris
✓ Go on a trip overseas with my whole family
✗ Take a hot-air balloon ride
✓ Be in a submarine
✗ Swim a mile
✗ Run a half marathon
✗ Scuba dive
✓ Learn to ski
✓ Surf in Hawaii
✓ Fly an airplane
✓ Learn to drive a car
✗ Get a PhD (in CS, Neuroscience, or Psychology)
✗ Body transformation
✓ Dance on stage at a concert (thanks Flo Rida!)
✗ Ride a horse in Mongolia
✓ Publish a Python package
✗ Create my own programming language
✗ Start a scholarship to support brave young kids
✗ Volunteer 1000 hours to help to the elderlies
✗ Get involved in a publishing house that focuses on math, science, and engineering books
✗ Start a research lab
✓ Take a walk in the rain
✓ Eat at a 3 Michelin star restaurant
✓ Ask a stranger out (he said no)
✓ Invite a stranger to my home (CouchSurfing)
✗ Sleep in a castle
✓ Sleep outside on the beach, under the sky (Eilat, Israel)
✓ Go on an African safari
✓ Camp in a desert
✗ See auroras
✓ Learn to salsa
✗ Learn to play a music instrument (tried 3x)
✗ Zero gravity
✓ Work in a casino
✓ Do stand-up
✓ Travel Southeast Asia
✓ Hitchhike across Africa (Egypt to Mozambique)
✗ Spend at least a month in Western Africa
✓ Hike Los Andes
✓ Visit South Omo valley, Ethiopia
✗ Sail around the Caribbean
✗ Drink vodka in Russia
✗ Eat sushi in Japan
✗ Travel around Eastern Europe
✓ See Kashmir
✗ Visit Mecca
✓ Do the Bible tour: Jerusalem, lake of Galilee, Jordan river, Bethlehem, Nazareth
✗ Stay with an Amazonian tribe
✓ Visit an Amish community
✗ Visit Vatican
✗ Visit Tehran
✗ Visit Sicily
✗ Visit 100 countries (~40% done)
✗ Go to South Pole or North Pole
✓ Climb Great Pyramid of Giza, Egypt
✗ Climb Great wall, China
✗ Hike to Everest base camp
✗ Reed Dance, Swaziland
✗ Burning Man, the US
✗ Carnival in Brazil
✓ Watch a Broadway show in New York
✓ Pashut Festival, Israel
✓ Laos’ new year
✗ Watch bullfight in Spain
✗ Watch a soccer game at Camp Nou (Old Trafford is fine too)
✓ Visit Googleplex
✗ Speak at TED
✗ Meet the Pope
✗ Meet a prince
✗ Meet JK Rowling
✓ See a comet
✓ Meet Dalai Lama
✗ Have my own ice cream flavor
~ Be awesome
~ Be kind
s
  </body>
</html>
{% endhighlight %}
