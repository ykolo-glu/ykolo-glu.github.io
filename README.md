# Yusuf Kologlu

## Persönliches
[Persönliche Infos](private.md)

## Berufserfahrung
* Samstagsaushilfe Bauhaus
* Lagerarbeit DM
* Praktikum efsta

## Programmierkenntnisse
* C
* C#
* Python
* Java
* Javascript
* SQL
* Vue

## Beispiel Code-Snippet
```
 public Scene loadScene(String filepath, boolean cacheLastUsedScene, boolean useCachedScene) throws IOException {

        Scene scene = null;
        System.out.println("method loadScene called with: filepath = " + filepath + ", cacheLastUsedScene = " + cacheLastUsedScene + ", useCachedScene = " + useCachedScene + "");
        boolean cachedSceneNotFound = false;
        if(useCachedScene){
            scene = getSceneFromFilepath(filepath);
            System.out.println("Suche cached Scene für: " + filepath);
            System.out.println("Gefundene Scene: " + scene);
            System.out.println("Alle Scenes im Cache: " + getScenes().keySet());
            if(scene == null){
                cachedSceneNotFound = true;
            }
        }
        if(!useCachedScene || cachedSceneNotFound){
            getScenes().remove(filepath);

            URL fxml = null;

            if(resourceClass != null){

                String filePathWithClassPath = resourceClass.getPackage().getName().replace(".", "/") + "/" + filepath;
                fxml = fxmlHelper(filePathWithClassPath);
            }

            if (fxml == null) {
                fxml = fxmlHelper(filepath);
            }

            if (fxml == null) {
                fxml = Thread.currentThread()
                        .getContextClassLoader()
                        .getResource(filepath + ".fxml");
            }

            if (fxml == null) {
                fxml = SceneManager.class.getResource("/" + filepath + ".fxml");
            }

            if (fxml == null) {
                throw new IllegalArgumentException(
                        "FXML not found: " + filepath + ".fxml"
                );
            }

            FXMLLoader loader = new FXMLLoader(fxml);
            scene = new Scene(loader.load());
        }

        getScenes().put(filepath, scene);
        if(getLastUsedFilepath() != null && !getLastUsedFilepath().isEmpty() && !cacheLastUsedScene){
            getScenes().remove(getLastUsedFilepath());
        }

        setLastUsedFilepath(filepath);

        return scene;
    }
```
