find_file(
    JUPYTER_BOOK_EXECUTABLE
    NAME jupyter-book${CMAKE_EXECUTABLE_SUFFIX}
    REQUIRED
)

set(MD_SOURCES
    index.md
    general/about.md
    general/software.md
    practicals/chapter_1.md
    practicals/chapter_2.md
    practicals/chapter_3.md
)

add_custom_command(
    DEPENDS ${MD_SOURCES}
    OUTPUT _build/html/index.html
    COMMAND
        ${JUPYTER_BOOK_EXECUTABLE} build
            ${CMAKE_CURRENT_SOURCE_DIR} --path-output ${CMAKE_CURRENT_BINARY_DIR} --builder html --all -W
)

add_custom_target(
    course-html
    ALL
    DEPENDS _build/html/index.html
)

add_custom_command(
    DEPENDS ${MD_SOURCES}
    OUTPUT _build/latex/geo4_4436.pdf
    COMMAND
        ${JUPYTER_BOOK_EXECUTABLE} build
            ${CMAKE_CURRENT_SOURCE_DIR} --path-output ${CMAKE_CURRENT_BINARY_DIR} --builder pdflatex --all
)

add_custom_target(
    course-pdf
    DEPENDS _build/latex/geo4_4436.pdf
)

add_custom_command(
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/_build/html/index.html
    OUTPUT ${CMAKE_BINARY_DIR}/course_html.zip
    COMMAND
        ${CMAKE_COMMAND} -E tar "cf" "${CMAKE_BINARY_DIR}/course_html.zip" --format=zip
        html/
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/_build
)

add_custom_target(
    course-html-zip
    ALL
    DEPENDS ${CMAKE_BINARY_DIR}/course_html.zip
)
