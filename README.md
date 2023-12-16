# ClassSearchManager.java


## Usage
```java
import java.util.List;

public class MainClassSearchApp {

    public static void main(String[] args) {
        String packageName = "your.package.name"; // Değiştirilmesi gereken paket adı
        String keyword = "YourKeyword"; // Değiştirilmesi gereken anahtar kelime

        List<Class<?>> startsWithClasses = ClassSearchManager.getClassesWithKeyword(packageName, keyword, ClassSearchManager.SearchType.STARTSWITH);
        System.out.println("Classes starting with " + keyword + ": " + startsWithClasses);

        List<Class<?>> containsClasses = ClassSearchManager.getClassesWithKeyword(packageName, keyword, ClassSearchManager.SearchType.CONTAINS);
        System.out.println("Classes containing " + keyword + ": " + containsClasses);

        List<Class<?>> endsWithClasses = ClassSearchManager.getClassesWithKeyword(packageName, keyword, ClassSearchManager.SearchType.ENDSWITH);
        System.out.println("Classes ending with " + keyword + ": " + endsWithClasses);
    }
}
```
