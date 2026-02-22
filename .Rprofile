source("renv/activate.R")
options(styler.width = 120)

if (nzchar(system.file(package = "lintr"))) {
  setHook(packageEvent("lintr", "onLoad"), function(...) {
    original_lint <- lintr::lint
    assignInNamespace(
      "lint",
      function(..., parse_settings = TRUE) {
        original_lint(..., parse_settings = parse_settings)
      },
      ns = "lintr"
    )
  })
}
