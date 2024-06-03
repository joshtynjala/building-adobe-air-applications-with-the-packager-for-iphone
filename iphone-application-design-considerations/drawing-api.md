# Drawing API

<div>

Try to avoid using the ActionScript drawing API (the Graphics class) to create
graphics. Using the drawing API creates objects dynamically on the stage, then
renders them to the rasterizer. If possible, create those objects statically in
authoring time on the stage instead.

Objects created using drawing APIs, when repeatedly called, are destroyed and
recreated every time ActionScript is executed. However, static objects reside in
memory through different timelines.

</div>

<div>

<div>

</div>

</div>
