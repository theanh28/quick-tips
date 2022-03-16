Vega lite API
  * Brush (e.g.: `const brush = vl.selectInterval().encodings('x')`
    1. `<mark>.select(brush)` = allow choosing interval on <mark>
    2. `<mark>.encode(vl.color().value('any color, recommend 'lightgrey' ')` = turn every thing to that color
      ** 1 and 2 usualy used together as `<mark>.select(brush).encode(vl.color().value('lightgrey'))` to create a layer of grey mark for interval selection
    3. `vl.filter(brush)` = only keep data points that suffice brush
    4. `vl.transform(vl.filter(brush))` = create a mark that only has data points respecting brush filter
      *** 1, 2, 4 used together in a layer:
        ```
        vl.layer(
          <mark>.select(brush).encode(vl.color().value('lightgrey')),
          <mark>.transform(vl.filter(brush))
        )
        ```
        for a lower layer of grey mark for interval selection and a upper layer of only points that suffice brush filter with bold color.
        
    5. `vl.encode(vl.opacity().if(brush, vl.value(1)).value(.1)` = opacity channel. Full opacity with brush: normally all points, or only in some interval when selected. 0.1 opacity otherwise.
