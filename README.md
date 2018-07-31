# scala-mill-cross

```scala
trait Common extends ScalaModule {
def scalaVersion = "2.12.6"
def ivyDeps = super.ivyDeps() ++ Agg(
// your common deps here in the format ivy"GroupId::ArtifactId::version"
)
def sources = T.sources(
millSourcePath / "src",
millSourcePath / up / "shared" / "src"
)
}

object jvm extends Common {
def ivyDeps = super.ivyDeps() ++ Agg(
// your server deps here in the format ivy"GroupId::ArtifactId:version"
)
}

object js extends ScalaJSModule with Common {
def scalaJSVersion = "0.6.23"
def ivyDeps = super.ivyDeps() ++ Agg(
// your client deps here in the format ivy"GroupId::ArtifactId::version"
)
}

object shared extends Common // it is a dummy module only for Intellij Idea Integration
```
