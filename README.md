# Vaadin Add-on html2canvas project

### Deployment

Starting the test/demo server:
```
mvn jetty:run
```
This deploys demo at http://localhost:8080
 
### Demo
    class Testview{
        Button button = new Button("Click here");
        button.addClickListener(l -> {
            CompletableFuture<String> completableFuture = HTML2CANVAS.takeScreenShot(button.getElement());
            completableFuture.thenRun(() -> {
                try {
                    Image image = new Image(completableFuture.get(), "adfs");
                    add(image);
                } catch (InterruptedException | ExecutionException ignored) {
                }
            });
        });
        add(button);
    }