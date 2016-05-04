cmake_minimum_required(VERSION 3.5)
project(cufflinks)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++03")
include_directories(src)

set(SOURCE_FILES
        src/Eigen/Dense
        src/lemon/bits/alteration_notifier.h
        src/lemon/bits/array_map.h
        src/lemon/bits/base_extender.h
        src/lemon/bits/debug_map.h
        src/lemon/bits/default_map.h
        src/lemon/bits/graph_adaptor_extender.h
        src/lemon/bits/graph_extender.h
        src/lemon/bits/invalid.h
        src/lemon/bits/map_extender.h
        src/lemon/bits/path_dump.h
        src/lemon/bits/traits.h
        src/lemon/bits/utility.h
        src/lemon/bits/variant.h
        src/lemon/bits/vector_map.h
        src/lemon/concepts/bpugraph.h
        src/lemon/concepts/graph.h
        src/lemon/concepts/graph_components.h
        src/lemon/concepts/heap.h
        src/lemon/concepts/maps.h
        src/lemon/concepts/matrix_maps.h
        src/lemon/concepts/path.h
        src/lemon/concepts/ugraph.h
        src/lemon/bfs.h
        src/lemon/bin_heap.h
        src/lemon/bipartite_matching.h
        src/lemon/bucket_heap.h
        src/lemon/concept_check.h
        src/lemon/dfs.h
        src/lemon/error.h
        src/lemon/fib_heap.h
        src/lemon/graph_adaptor.h
        src/lemon/graph_utils.h
        src/lemon/list_graph.h
        src/lemon/maps.h
        src/lemon/math.h
        src/lemon/smart_graph.h
        src/lemon/tolerance.h
        src/lemon/topology.h
        src/locfit/adap.c
        src/locfit/ar_funs.c
        src/locfit/arith.c
        src/locfit/band.c
        src/locfit/c_args.c
        src/locfit/c_plot.c
        src/locfit/cmd.c
        src/locfit/dens_haz.c
        src/locfit/dens_int.c
        src/locfit/dens_odi.c
        src/locfit/density.c
        src/locfit/design.h
        src/locfit/dist.c
        src/locfit/ev_atree.c
        src/locfit/ev_interp.c
        src/locfit/ev_kdtre.c
        src/locfit/ev_main.c
        src/locfit/ev_trian.c
        src/locfit/family.c
        src/locfit/fitted.c
        src/locfit/frend.c
        src/locfit/help.c
        src/locfit/imatlb.h
        src/locfit/lf_dercor.c
        src/locfit/lf_fitfun.c
        src/locfit/lf_robust.c
        src/locfit/lf_vari.c
        src/locfit/lfcons.h
        src/locfit/lfd.c
        src/locfit/lffuns.h
        src/locfit/lfstr.c
        src/locfit/lfstruc.h
        src/locfit/lfwin.h
        src/locfit/linalg.c
        src/locfit/local.h
        src/locfit/locfit.c
        src/locfit/m_chol.c
        src/locfit/m_eigen.c
        src/locfit/m_jacob.c
        src/locfit/m_max.c
        src/locfit/makecmd.c
        src/locfit/math.c
        src/locfit/minmax.c
        src/locfit/mutil.h
        src/locfit/nbhd.c
        src/locfit/pcomp.c
        src/locfit/pout.c
        src/locfit/preplot.c
        src/locfit/random.c
        src/locfit/readfile.c
        src/locfit/scb.c
        src/locfit/scb_cons.c
        src/locfit/simul.c
        src/locfit/solve.c
        src/locfit/startlf.c
        src/locfit/strings.c
        src/locfit/vari.cpp
        src/locfit/vari.hpp
        src/locfit/wdiag.c
        src/locfit/weight.c
        src/abundances.cpp
        src/abundances.h
        src/assemble.cpp
        src/assemble.h
        src/biascorrection.cpp
        src/biascorrection.h
        src/bundles.cpp
        src/bundles.h
        src/clustering.cpp
        src/clustering.h
        src/codons.cpp
        src/codons.h
        src/common.cpp
        src/common.h
        #    src/compress_gtf.cpp
        #    src/cuffcluster.cpp
        #    src/cuffcompare.cpp
        #    src/cuffdiff.cpp
        #    src/cufflinks.cpp
        #    src/cuffnorm.cpp
        #    src/cuffquant.cpp
        #    src/differential.cpp
        #    src/differential.h
        src/filters.cpp
        src/filters.h
        src/GArgs.cpp
        src/GArgs.h
        src/GBase.cpp
        src/GBase.h
        src/gdna.cpp
        src/gdna.h
        src/genes.cpp
        src/genes.h
        src/GFaSeqGet.cpp
        src/GFaSeqGet.h
        src/GFastaIndex.cpp
        src/GFastaIndex.h
        src/gff.cpp
        src/gff.h
        #        src/gff_utils.cpp
        src/gff_utils.h
        #        src/gffread.cpp
        src/GHash.hh
        src/GList.hh
        src/graph_optimize.cpp
        src/graph_optimize.h
        src/GStr.cpp
        src/GStr.h
        #    src/gtf_reads.cpp
        #    src/gtf_to_sam.cpp
        src/gtf_tracking.cpp
        src/gtf_tracking.h
        src/GVec.hh
        src/hits.cpp
        src/hits.h
        src/jensen_shannon.cpp
        src/jensen_shannon.h
        src/matching_merge.cpp
        src/matching_merge.h
        src/multireads.cpp
        src/multireads.h
        src/negative_binomial_distribution.h
        src/progressbar.h
        src/replicates.cpp
        src/replicates.h
        src/rounding.h
        src/sampling.cpp
        src/sampling.h
        src/scaffold_graph.cpp
        src/scaffold_graph.h
        src/scaffolds.cpp
        src/scaffolds.h
        src/tokenize.cpp
        src/tokenize.h
        src/tracking.cpp
        src/tracking.h
        src/transitive_closure.h
        src/transitive_reduction.h
        src/update_check.h
        )


find_package(Boost COMPONENTS system serialization thread REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})

# cufflinks
add_executable(cufflinks src/cufflinks.cpp ${SOURCE_FILES})
target_link_libraries(cufflinks ${Boost_LIBRARIES} bam z pthread)

# cuffdiff
add_executable(cuffdiff src/cuffdiff.cpp ${SOURCE_FILES} src/differential.cpp)
target_link_libraries(cuffdiff ${Boost_LIBRARIES} bam z pthread)

# cuffnorm
add_executable(cuffnorm src/cuffnorm.cpp ${SOURCE_FILES} src/differential.cpp)
target_link_libraries(cuffnorm ${Boost_LIBRARIES} bam z pthread)

# cuffquant
add_executable(cuffquant src/cuffquant.cpp ${SOURCE_FILES})
target_link_libraries(cuffquant ${Boost_LIBRARIES} bam z pthread)
