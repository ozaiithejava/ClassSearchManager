# ClassSearchManager.java


## Usage
```java
import java.io.File;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

public class ClassSearchManager {

    public static List<Class<?>> getClassesWithKeyword(String packageName, String keyword, SearchType searchType) {
        List<Class<?>> matchingClasses = new ArrayList<>();
        try {
            String path = packageName.replace('.', '/');
            File packageDir = new File(ClassLoader.getSystemClassLoader().getResource(path).getFile());
            File[] files = packageDir.listFiles();
            if (files != null) {
                for (File file : files) {
                    if (file.isFile() && file.getName().endsWith(".class")) {
                        String className = packageName + "." + file.getName().replace(".class", "");
                        if (isClassMatchingKeyword(className, keyword, searchType)) {
                            Class<?> clazz = Class.forName(className);
                            matchingClasses.add(clazz);
                        }
                    }
                }
            }
        } catch (ClassNotFoundException | IOException e) {
            e.printStackTrace();
        }
        return matchingClasses;
    }

    private static boolean isClassMatchingKeyword(String className, String keyword, SearchType searchType) {
        switch (searchType) {
            case STARTSWITH:
                return className.startsWith(keyword);
            case CONTAINS:
                return className.contains(keyword);
            case ENDSWITH:
                return className.endsWith(keyword);
            default:
                return false;
        }
    }

    public enum SearchType {
        STARTSWITH, CONTAINS, ENDSWITH
    }
}
```
