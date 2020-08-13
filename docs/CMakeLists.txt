option(USE_SPHINX "Use Sphinx to build the documentation" ON)

find_package(Doxygen OPTIONAL_COMPONENTS dot mscgen dia)

##FIXME MOVE THIS
macro(set_if_not variable value)
  if(NOT DEFINED ${variable})
    set(${variable} ${value})
  endif()
endmacro()

if(NOT DOXYGEN_FOUND)
  message(STATUS "Doxygen is needed to build the documentation.")
  return()
endif()

if(USE_SPHINX)
  find_package(Sphinx)
  if(NOT SPHINX_FOUND)
    message(STATUS "Sphinx is needed to build the documentation.")
    return()
  endif()

  find_package(Breathe)
  if(NOT BREATHE_FOUND)
    message(STATUS "Breathe is needed to build the documentation.")
    return()
  endif()
  set(DOXYGEN_GENERATE_XML "YES")
endif()

##MOVE THIS TO DOXYGEN.cmake
#Default value for Doxygen 1.8.18
macro(set_default_doxyfile)
  set_if_not(DOXYGEN_PROJECT_NAME ${CMAKE_PROJECT_NAME})
  set_if_not(DOXYGEN_PROJECT_NUMBER ${CMAKE_PROJECT_VERSION})
  set_if_not(DOXYGEN_PROJECT_BRIEF ${CMAKE_PROJECT_DESCRIPTION})
  set_if_not(DOXYGEN_DOXYFILE_ENCODING "UTF-8")
  set_if_not(DOXYGEN_CREATE_SUBDIRS "NO")
  set_if_not(DOXYGEN_ALLOW_UNICODE_NAMES "NO")
  set_if_not(DOXYGEN_OUTPUT_LANGUAGE "English")
  set_if_not(DOXYGEN_OUTPUT_TEXT_DIRECTION "None")
  set_if_not(DOXYGEN_BRIEF_MEMBER_DESC "YES")
  set_if_not(DOXYGEN_REPEAT_BRIEF "YES")
  set_if_not(DOXYGEN_ABBREVIATE_BRIEF "\"The $name class\" \\\\
                         \"The $name widget\" \\\\
                         \"The $name file\" \\\\
                         is \\\\
                         provides \\\\
                         specifies \\\\
                         contains \\\\
                         represents \\\\
                         a \\\\
                         an \\\\
                         the")
  set_if_not(DOXYGEN_ALWAYS_DETAILED_SEC "NO")
  set_if_not(DOXYGEN_INLINE_INHERITED_MEMB "NO")
  set_if_not(DOXYGEN_FULL_PATH_NAMES "YES")
  set_if_not(DOXYGEN_SHORT_NAMES "NO")
  set_if_not(DOXYGEN_JAVADOC_AUTOBRIEF "NO")
  set_if_not(DOXYGEN_JAVADOC_BANNER "NO")
  set_if_not(DOXYGEN_QT_AUTOBRIEF "NO")
  set_if_not(DOXYGEN_MULTILINE_CPP_IS_BRIEF "NO")
  set_if_not(DOXYGEN_INHERIT_DOCS "YES")
  set_if_not(DOXYGEN_SEPARATE_MEMBER_PAGES "NO")
  set_if_not(DOXYGEN_TAB_SIZE "4")
  set_if_not(DOXYGEN_OPTIMIZE_OUTPUT_FOR_C "NO")
  set_if_not(DOXYGEN_OPTIMIZE_OUTPUT_JAVA "NO")
  set_if_not(DOXYGEN_OPTIMIZE_FOR_FORTRAN "NO")
  set_if_not(DOXYGEN_OPTIMIZE_OUTPUT_VHDL "NO")
  set_if_not(DOXYGEN_OPTIMIZE_OUTPUT_SLICE "NO")
  set_if_not(DOXYGEN_MARKDOWN_SUPPORT "YES")
  set_if_not(DOXYGEN_TOC_INCLUDE_HEADINGS "5")
  set_if_not(DOXYGEN_AUTOLINK_SUPPORT "YES")
  set_if_not(DOXYGEN_BUILTIN_STL_SUPPORT "NO")
  set_if_not(DOXYGEN_CPP_CLI_SUPPORT        "NO")
  set_if_not(DOXYGEN_SIP_SUPPORT            "NO")
  set_if_not(DOXYGEN_IDL_PROPERTY_SUPPORT   "YES")
  set_if_not(DOXYGEN_DISTRIBUTE_GROUP_DOC   "NO")
  set_if_not(DOXYGEN_GROUP_NESTED_COMPOUNDS "NO")
  set_if_not(DOXYGEN_SUBGROUPING            "YES")
  set_if_not(DOXYGEN_INLINE_GROUPED_CLASSES "NO")
  set_if_not(DOXYGEN_INLINE_SIMPLE_STRUCTS  "NO")
  set_if_not(DOXYGEN_TYPEDEF_HIDES_STRUCT   "NO")
  set_if_not(DOXYGEN_LOOKUP_CACHE_SIZE      "0")
  set_if_not(DOXYGEN_EXTRACT_ALL            "NO")
  set_if_not(DOXYGEN_EXTRACT_PRIVATE        "NO")
  set_if_not(DOXYGEN_EXTRACT_PRIV_VIRTUAL   "NO")
  set_if_not(DOXYGEN_EXTRACT_PACKAGE        "NO")
  set_if_not(DOXYGEN_EXTRACT_STATIC         "NO")
  set_if_not(DOXYGEN_EXTRACT_LOCAL_CLASSES  "YES")
  set_if_not(DOXYGEN_EXTRACT_LOCAL_METHODS  "NO")
  set_if_not(DOXYGEN_EXTRACT_ANON_NSPACES   "NO")
  set_if_not(DOXYGEN_HIDE_UNDOC_MEMBERS     "NO")
  set_if_not(DOXYGEN_HIDE_UNDOC_CLASSES     "NO")
  set_if_not(DOXYGEN_HIDE_FRIEND_COMPOUNDS  "NO")
  set_if_not(DOXYGEN_HIDE_IN_BODY_DOCS      "NO")
  set_if_not(DOXYGEN_INTERNAL_DOCS          "NO")
  set_if_not(DOXYGEN_CASE_SENSE_NAMES       "YES")
  set_if_not(DOXYGEN_HIDE_SCOPE_NAMES       "NO")
  set_if_not(DOXYGEN_HIDE_COMPOUND_REFERENCE "NO")
  set_if_not(DOXYGEN_SHOW_INCLUDE_FILES     "YES")
  set_if_not(DOXYGEN_SHOW_GROUPED_MEMB_INC  "NO")
  set_if_not(DOXYGEN_FORCE_LOCAL_INCLUDES   "NO")
  set_if_not(DOXYGEN_INLINE_INFO            "YES")
  set_if_not(DOXYGEN_SORT_MEMBER_DOCS       "YES")
  set_if_not(DOXYGEN_SORT_BRIEF_DOCS        "NO")
  set_if_not(DOXYGEN_SORT_MEMBERS_CTORS_1ST "NO")
  set_if_not(DOXYGEN_SORT_GROUP_NAMES       "NO")
  set_if_not(DOXYGEN_SORT_BY_SCOPE_NAME     "NO")
  set_if_not(DOXYGEN_STRICT_PROTO_MATCHING  "NO")
  set_if_not(DOXYGEN_GENERATE_TODOLIST      "YES")
  set_if_not(DOXYGEN_GENERATE_TESTLIST      "YES")
  set_if_not(DOXYGEN_GENERATE_BUGLIST       "YES")
  set_if_not(DOXYGEN_GENERATE_DEPRECATEDLIST "YES")
  set_if_not(DOXYGEN_MAX_INITIALIZER_LINES  "30")
  set_if_not(DOXYGEN_SHOW_USED_FILES        "YES")
  set_if_not(DOXYGEN_SHOW_FILES             "YES")
  set_if_not(DOXYGEN_SHOW_NAMESPACES        "YES")
  set_if_not(DOXYGEN_QUIET                  "NO")
  set_if_not(DOXYGEN_WARNINGS               "YES")
  set_if_not(DOXYGEN_WARN_IF_UNDOCUMENTED   "YES")
  set_if_not(DOXYGEN_WARN_IF_DOC_ERROR      "YES")
  set_if_not(DOXYGEN_WARN_NO_PARAMDOC       "NO")
  set_if_not(DOXYGEN_WARN_AS_ERROR          "NO")
  set_if_not(DOXYGEN_WARN_FORMAT            "\"$file:$line: $text\"")
  set_if_not(DOXYGEN_INPUT_ENCODING         "UTF-8")
  set_if_not(DOXYGEN_FILE_PATTERNS          "*.c \\\\
                         *.cc \\\\
                         *.cxx \\\\
                         *.cpp \\\\
                         *.c++ \\\\
                         *.java \\\\
                         *.ii \\\\
                         *.ixx \\\\
                         *.ipp \\\\
                         *.i++ \\\\
                         *.inl \\\\
                         *.idl \\\\
                         *.ddl \\\\
                         *.odl \\\\
                         *.h \\\\
                         *.hh \\\\
                         *.hxx \\\\
                         *.hpp \\\\
                         *.h++ \\\\
                         *.cs \\\\
                         *.d \\\\
                         *.php \\\\
                         *.php4 \\\\
                         *.php5 \\\\
                         *.phtml \\\\
                         *.inc \\\\
                         *.m \\\\
                         *.markdown \\\\
                         *.md \\\\
                         *.mm \\\\
                         *.dox \\\\
                         *.doc \\\\
                         *.txt \\\\
                         *.py \\\\
                         *.pyw \\\\
                         *.f90 \\\\
                         *.f95 \\\\
                         *.f03 \\\\
                         *.f08 \\\\
                         *.f18 \\\\
                         *.f \\\\
                         *.for \\\\
                         *.vhd \\\\
                         *.vhdl \\\\
                         *.ucf \\\\
                         *.qsf \\\\
                         *.ice")
  set_if_not(DOXYGEN_RECURSIVE              "NO")
  set_if_not(DOXYGEN_EXCLUDE_SYMLINKS       "NO")
  set_if_not(DOXYGEN_EXAMPLE_PATTERNS       "*")
  set_if_not(DOXYGEN_EXAMPLE_RECURSIVE      "NO")
  set_if_not(DOXYGEN_FILTER_SOURCE_FILES    "NO")
  set_if_not(DOXYGEN_SOURCE_BROWSER         "NO")
  set_if_not(DOXYGEN_INLINE_SOURCES         "NO")
  set_if_not(DOXYGEN_STRIP_CODE_COMMENTS    "YES")
  set_if_not(DOXYGEN_REFERENCED_BY_RELATION "NO")
  set_if_not(DOXYGEN_REFERENCES_RELATION    "NO")
  set_if_not(DOXYGEN_REFERENCES_LINK_SOURCE "YES")
  set_if_not(DOXYGEN_SOURCE_TOOLTIPS        "YES")
  set_if_not(DOXYGEN_USE_HTAGS              "NO")
  set_if_not(DOXYGEN_VERBATIM_HEADERS       "YES")
  set_if_not(DOXYGEN_ALPHABETICAL_INDEX     "YES")
  set_if_not(DOXYGEN_COLS_IN_ALPHA_INDEX    "5")
  set_if_not(DOXYGEN_GENERATE_HTML          "YES")
  set_if_not(DOXYGEN_HTML_OUTPUT            "html")
  set_if_not(DOXYGEN_HTML_FILE_EXTENSION    ".html")
  set_if_not(DOXYGEN_HTML_COLORSTYLE_HUE    "220")
  set_if_not(DOXYGEN_HTML_COLORSTYLE_SAT    "100")
  set_if_not(DOXYGEN_HTML_COLORSTYLE_GAMMA  "80")
  set_if_not(DOXYGEN_HTML_TIMESTAMP         "NO")
  set_if_not(DOXYGEN_HTML_DYNAMIC_MENUS     "YES")
  set_if_not(DOXYGEN_HTML_DYNAMIC_SECTIONS  "NO")
  set_if_not(DOXYGEN_HTML_INDEX_NUM_ENTRIES "100")
  set_if_not(DOXYGEN_GENERATE_DOCSET        "NO")
  set_if_not(DOXYGEN_DOCSET_FEEDNAME        "Doxygen generated docs")
  set_if_not(DOXYGEN_DOCSET_BUNDLE_ID       "org.doxygen.Project")
  set_if_not(DOXYGEN_DOCSET_PUBLISHER_ID    "org.doxygen.Publisher")
  set_if_not(DOXYGEN_DOCSET_PUBLISHER_NAME  "Publisher")
  set_if_not(DOXYGEN_GENERATE_HTMLHELP      "NO")
  set_if_not(DOXYGEN_GENERATE_CHI           "NO")
  set_if_not(DOXYGEN_BINARY_TOC             "NO")
  set_if_not(DOXYGEN_TOC_EXPAND             "NO")
  set_if_not(DOXYGEN_GENERATE_QHP           "NO")
  set_if_not(DOXYGEN_QHP_NAMESPACE          "org.doxygen.Project")
  set_if_not(DOXYGEN_QHP_VIRTUAL_FOLDER     "doc")
  set_if_not(DOXYGEN_GENERATE_ECLIPSEHELP   "NO")
  set_if_not(DOXYGEN_ECLIPSE_DOC_ID         "org.doxygen.Project")
  set_if_not(DOXYGEN_DISABLE_INDEX          "NO")
  set_if_not(DOXYGEN_GENERATE_TREEVIEW      "NO")
  set_if_not(DOXYGEN_ENUM_VALUES_PER_LINE   "4")
  set_if_not(DOXYGEN_TREEVIEW_WIDTH         "250")
  set_if_not(DOXYGEN_EXT_LINKS_IN_WINDOW    "NO")
  set_if_not(DOXYGEN_HTML_FORMULA_FORMAT    "png")
  set_if_not(DOXYGEN_FORMULA_FONTSIZE       "10")
  set_if_not(DOXYGEN_FORMULA_TRANSPARENT    "YES")
  set_if_not(DOXYGEN_USE_MATHJAX            "NO")
  set_if_not(DOXYGEN_MATHJAX_FORMAT         "HTML-CSS")
  set_if_not(DOXYGEN_MATHJAX_RELPATH        "https://cdn.jsdelivr.net/npm/mathjax@2")
  set_if_not(DOXYGEN_SEARCHENGINE           "YES")
  set_if_not(DOXYGEN_SERVER_BASED_SEARCH    "NO")
  set_if_not(DOXYGEN_EXTERNAL_SEARCH        "NO")
  set_if_not(DOXYGEN_SEARCHDATA_FILE        "searchdata.xml")
  set_if_not(DOXYGEN_GENERATE_LATEX         "YES")
  set_if_not(DOXYGEN_LATEX_OUTPUT           "latex")
  set_if_not(DOXYGEN_MAKEINDEX_CMD_NAME     "makeindex")
  set_if_not(DOXYGEN_LATEX_MAKEINDEX_CMD    "makeindex")
  set_if_not(DOXYGEN_COMPACT_LATEX          "NO")
  set_if_not(DOXYGEN_PAPER_TYPE             "a4")
  set_if_not(DOXYGEN_PDF_HYPERLINKS         "YES")
  set_if_not(DOXYGEN_USE_PDFLATEX           "YES")
  set_if_not(DOXYGEN_LATEX_BATCHMODE        "NO")
  set_if_not(DOXYGEN_LATEX_HIDE_INDICES     "NO")
  set_if_not(DOXYGEN_LATEX_SOURCE_CODE      "NO")
  set_if_not(DOXYGEN_LATEX_BIB_STYLE        "plain")
  set_if_not(DOXYGEN_LATEX_TIMESTAMP        "NO")
  set_if_not(DOXYGEN_GENERATE_RTF           "NO")
  set_if_not(DOXYGEN_RTF_OUTPUT             "rtf")
  set_if_not(DOXYGEN_COMPACT_RTF            "NO")
  set_if_not(DOXYGEN_RTF_HYPERLINKS         "NO")
  set_if_not(DOXYGEN_RTF_SOURCE_CODE        "NO")
  set_if_not(DOXYGEN_GENERATE_MAN           "NO")
  set_if_not(DOXYGEN_MAN_OUTPUT             "man")
  set_if_not(DOXYGEN_MAN_EXTENSION          ".3")
  set_if_not(DOXYGEN_MAN_LINKS              "NO")
  set_if_not(DOXYGEN_GENERATE_XML           "NO")
  set_if_not(DOXYGEN_XML_OUTPUT             "xml")
  set_if_not(DOXYGEN_XML_PROGRAMLISTING     "YES")
  set_if_not(DOXYGEN_XML_NS_MEMB_FILE_SCOPE "NO")
  set_if_not(DOXYGEN_GENERATE_DOCBOOK       "NO")
  set_if_not(DOXYGEN_DOCBOOK_OUTPUT         "docbook")
  set_if_not(DOXYGEN_DOCBOOK_PROGRAMLISTING "NO")
  set_if_not(DOXYGEN_GENERATE_AUTOGEN_DEF   "NO")
  set_if_not(DOXYGEN_GENERATE_PERLMOD       "NO")
  set_if_not(DOXYGEN_PERLMOD_LATEX          "NO")
  set_if_not(DOXYGEN_PERLMOD_PRETTY         "YES")
  set_if_not(DOXYGEN_ENABLE_PREPROCESSING   "YES")
  set_if_not(DOXYGEN_MACRO_EXPANSION        "NO")
  set_if_not(DOXYGEN_EXPAND_ONLY_PREDEF     "NO")
  set_if_not(DOXYGEN_SEARCH_INCLUDES        "YES")
  set_if_not(DOXYGEN_SKIP_FUNCTION_MACROS   "YES")
  set_if_not(DOXYGEN_ALLEXTERNALS           "NO")
  set_if_not(DOXYGEN_EXTERNAL_GROUPS        "YES")
  set_if_not(DOXYGEN_EXTERNAL_PAGES         "YES")
  set_if_not(DOXYGEN_CLASS_DIAGRAMS         "YES")
  set_if_not(DOXYGEN_HIDE_UNDOC_RELATIONS   "YES")
  set_if_not(DOXYGEN_HAVE_DOT               "NO")
  set_if_not(DOXYGEN_DOT_NUM_THREADS        "0")
  set_if_not(DOXYGEN_DOT_FONTNAME           "Helvetica")
  set_if_not(DOXYGEN_DOT_FONTSIZE           "10")
  set_if_not(DOXYGEN_CLASS_GRAPH            "YES")
  set_if_not(DOXYGEN_COLLABORATION_GRAPH    "YES")
  set_if_not(DOXYGEN_GROUP_GRAPHS           "YES")
  set_if_not(DOXYGEN_UML_LOOK               "NO")
  set_if_not(DOXYGEN_UML_LIMIT_NUM_FIELDS   "10")
  set_if_not(DOXYGEN_TEMPLATE_RELATIONS     "NO")
  set_if_not(DOXYGEN_INCLUDE_GRAPH          "YES")
  set_if_not(DOXYGEN_INCLUDED_BY_GRAPH      "YES")
  set_if_not(DOXYGEN_CALL_GRAPH             "NO")
  set_if_not(DOXYGEN_CALLER_GRAPH           "NO")
  set_if_not(DOXYGEN_GRAPHICAL_HIERARCHY    "YES")
  set_if_not(DOXYGEN_DIRECTORY_GRAPH        "YES")
  set_if_not(DOXYGEN_DOT_IMAGE_FORMAT       "png")
  set_if_not(DOXYGEN_INTERACTIVE_SVG        "NO")
  set_if_not(DOXYGEN_DOT_GRAPH_MAX_NODES    "50")
  set_if_not(DOXYGEN_MAX_DOT_GRAPH_DEPTH    "0")
  set_if_not(DOXYGEN_DOT_TRANSPARENT        "NO")
  set_if_not(DOXYGEN_DOT_MULTI_TARGETS      "NO")
  set_if_not(DOXYGEN_GENERATE_LEGEND        "YES")
  set_if_not(DOXYGEN_DOT_CLEANUP            "YES")
endmacro()

set(DOXYGEN_INPUT "${CMAKE_SOURCE_DIR}/src ${CMAKE_SOURCE_DIR}/include")
set(DOXYGEN_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/docs/Doxygen")

function(generate_doxyfile doxyfilein doxyfileout)



  set_default_doxyfile()
  if(DOXYGEN_GENERATE_LATEX)
    find_package(LATEX COMPONENTS PDFLATEX)
    if(NOT LATEX_PDFLATEX_FOUND)
      message(ERROR "PdfLaTeX is needed to build the latex documentation.")
      set(DOXYGEN_GENERATE_LATEX "NO")
    else()
      set(DOXYGEN_LATEX_CMD_NAME ${PDFLATEX_COMPILER})
    endif()
  endif()


  set(OUTPUT "")
  if(DOXYGEN_GENERATE_HTML)
    set(DOXYGEN_OUPUTS_HTML "${DOXYGEN_OUTPUT_DIRECTORY}/${DOXYGEN_HTML_OUTPUT}/index${DOXYGEN_HTML_FILE_EXTENSION}")
    install(DIRECTORY "${DOXYGEN_OUTPUT_DIRECTORY}/html" DESTINATION "${CMAKE_INSTALL_PREFIX}/docs/Doxygen" MESSAGE_NEVER)
  endif()

  if(DOXYGEN_GENERATE_XML)

    set(DOXYGEN_OUPUTS_XML "${DOXYGEN_OUTPUT_DIRECTORY}/${DOXYGEN_XML_OUTPUT}/index.xml")

  endif()

  if(DOXYGEN_GENERATE_LATEX)
    set(DOXYGEN_OUPUTS_LATEX "${DOXYGEN_OUTPUT_DIRECTORY}/${DOXYGEN_LATEX_OUTPUT}/refman.tex")
    set(doxy_latex_index_file "${DOXYGEN_OUTPUT_DIRECTORY}/${DOXYGEN_LATEX_OUTPUT}/refman.pdf")
  endif()

  string(CONCAT OUTPUT ${DOXYGEN_OUPUTS_HTML} " " ${DOXYGEN_OUPUTS_LATEX} " " ${DOXYGEN_OUPUTS_XML})

  configure_file(${doxyfilein} ${doxyfileout} @ONLY)
  add_custom_command(OUTPUT ${OUTPUT} COMMAND Doxygen::doxygen ${doxyfileout} MAIN_DEPENDENCY ${doxyfilein} ${doxyfileout} COMMENT "Running Doxygen")
  add_custom_target(doc ALL DEPENDS ${OUTPUT})

  if(DOXYGEN_GENERATE_LATEX)
    add_custom_command(OUTPUT ${doxy_latex_index_file} COMMAND ${PDFLATEX_COMPILER} -interaction=batchmode ${DOXYGEN_OUPUTS_LATEX} COMMAND ${PDFLATEX_COMPILER} -interaction=batchmode ${DOXYGEN_OUPUTS_LATEX} COMMAND ${PDFLATEX_COMPILER} -interaction=batchmode ${DOXYGEN_OUPUTS_LATEX} COMMAND ${PDFLATEX_COMPILER} -interaction=batchmode ${DOXYGEN_OUPUTS_LATEX} BYPRODUCTS ${doxy_latex_index_file} MAIN_DEPENDENCY ${OUTPUT} COMMENT "Generating Latex documentation" WORKING_DIRECTORY "${DOXYGEN_OUTPUT_DIRECTORY}/${DOXYGEN_LATEX_OUTPUT}")
    add_custom_target(doc_latex ALL DEPENDS ${doxy_latex_index_file})
    install(FILES "${doxy_latex_index_file}" DESTINATION "${CMAKE_INSTALL_PREFIX}/docs/Doxygen" RENAME "${PROJECT_NAME}Manual.pdf")
  endif()
endfunction()

generate_doxyfile("${CMAKE_SOURCE_DIR}/docs/Doxyfile.in" "${PROJECT_BINARY_DIR}/docs/Doxyfile")


if(USE_SPHINX)
  if(DOXYGEN_GENERATE_XML)
    set_if_not(DOXYGEN_XML_OUTPUT  "${DOXYGEN_OUTPUT_DIRECTORY}/xml")
  endif()
  set(SPHINX_CONFIG_OUTPUT_DIR "${CMAKE_CURRENT_BINARY_DIR}")
  set(SPHINX_CONFIG_IN "${CMAKE_CURRENT_SOURCE_DIR}/conf.py.in")
  set(SPHINX_BUILD "${CMAKE_CURRENT_BINARY_DIR}/Sphinx")
  set(SPHINX_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}")
  set(PROJECT_AUTHOR "Me")
  set(COPYRIGHT_YEAR "2020")
  set(SPHINX_INDEX_FILE ${SPHINX_BUILD}/index.html)
  configure_file(${SPHINX_CONFIG_IN} "${SPHINX_CONFIG_OUTPUT_DIR}/conf.py" @ONLY)


  add_custom_command(OUTPUT ${SPHINX_INDEX_FILE}
                     COMMAND ${SPHINX_EXECUTABLE} -b html
                     # Tell Breathe where to find the Doxygen output
                     #-Dbreathe_projects.CatCutifier=${DOXYGEN_OUTPUT_DIR}/xml
                     ${SPHINX_SOURCE} ${SPHINX_BUILD} -c ${SPHINX_CONFIG_OUTPUT_DIR}
                     WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
                     DEPENDS
                     # Other docs files you want to track should go here (or in some variable)
                     ${CMAKE_CURRENT_SOURCE_DIR}/index.rst
                     ${CMAKE_CURRENT_SOURCE_DIR}/api/
                     doc
                     MAIN_DEPENDENCY "${SPHINX_CONFIG_OUTPUT_DIR}/conf.py"
                     COMMENT "Generating documentation with Sphinx")

  # Nice named target so we can run the job easily
  add_custom_target(Sphinx ALL DEPENDS ${SPHINX_INDEX_FILE})
  install(DIRECTORY "${SPHINX_BUILD}/" DESTINATION "${CMAKE_INSTALL_PREFIX}/docs/Sphinx" MESSAGE_NEVER)
endif()








